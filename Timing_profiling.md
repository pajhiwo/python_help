
## Timing and Profiling

Before we start optimizing anything, we first need to find out which parts of our code actually slow down the whole program. Sometimes the bottleneck of the program might be obvious, but in case you don't know where it is, then here are options you have for finding out:

_Note: This is the program I will be using for demonstration purposes, it computes `e` to power of `X` (taken from Python docs):_

```
# slow_program.py
from decimal import *

def exp(x):
    getcontext().prec += 2
    i, lasts, s, fact, num = 0, 0, 1, 1, 1
    while s != lasts:
        lasts = s
        i += 1
        fact *= i
        num *= x
        s += num / fact
    getcontext().prec -= 2
    return +s

exp(Decimal(150))
exp(Decimal(400))
exp(Decimal(3000))
```

### The Laziest "Profiling"

First off, the simplest and honestly very lazy solution - Unix `time` command:

```
~ $ time python3.8 slow_program.py

real 0m11,058s
user 0m11,050s
sys  0m0,008s
```

This could work, if you just want to time your whole program, which is usually not enough...

### The Most Detailed Profiling

On the other end of spectrum is `cProfile`, which will give you _too much_ information:

```
~ $ python3.8 -m cProfile -s time slow_program.py
         1297 function calls (1272 primitive calls) in 11.081 seconds

   Ordered by: internal time

   ncalls  tottime  percall  cumtime  percall filename:lineno(function)
        3   11.079    3.693   11.079    3.693 slow_program.py:4(exp)
        1    0.000    0.000    0.002    0.002 {built-in method _imp.create_dynamic}
      4/1    0.000    0.000   11.081   11.081 {built-in method builtins.exec}
        6    0.000    0.000    0.000    0.000 {built-in method __new__ of type object at 0x9d12c0}
        6    0.000    0.000    0.000    0.000 abc.py:132(__new__)
       23    0.000    0.000    0.000    0.000 _weakrefset.py:36(__init__)
      245    0.000    0.000    0.000    0.000 {built-in method builtins.getattr}
        2    0.000    0.000    0.000    0.000 {built-in method marshal.loads}
       10    0.000    0.000    0.000    0.000 <frozen importlib._bootstrap_external>:1233(find_spec)
      8/4    0.000    0.000    0.000    0.000 abc.py:196(__subclasscheck__)
       15    0.000    0.000    0.000    0.000 {built-in method posix.stat}
        6    0.000    0.000    0.000    0.000 {built-in method builtins.__build_class__}
        1    0.000    0.000    0.000    0.000 __init__.py:357(namedtuple)
       48    0.000    0.000    0.000    0.000 <frozen importlib._bootstrap_external>:57(_path_join)
       48    0.000    0.000    0.000    0.000 <frozen importlib._bootstrap_external>:59(<listcomp>)
        1    0.000    0.000   11.081   11.081 slow_program.py:1(<module>)
...
```

Here, we ran the testing script with `cProfile` module and `time` argument, so that lines are ordered by internal time (`cumtime`). This gives us _a lot_ of information, the lines you can see above are about 10% of the actual output. From this we can see that `exp` function is the culprit (_surprise, surprise_) and now we can get little more specific with timing and profiling...

### Timing Specific Functions

Now that we know where to direct our attention, we might want to time the slow function, without measuring rest of the code. For that we can use simple decorator:

```
def timeit_wrapper(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.perf_counter()  # Alternatively, you can use time.process_time()
        func_return_val = func(*args, **kwargs)
        end = time.perf_counter()
        print('{0:<10}.{1:<8} : {2:<8}'.format(func.__module__, func.__name__, end - start))
        return func_return_val
    return wrapper
```

This decorator can be then applied to function under test like so:

```
@timeit_wrapper
def exp(x):
    ...

print('{0:<10} {1:<8} {2:^8}'.format('module', 'function', 'time'))
exp(Decimal(150))
exp(Decimal(400))
exp(Decimal(3000))
```

This gives us output like this:

```
~ $ python3.8 slow_program.py
module     function   time
__main__  .exp      : 0.003267502994276583
__main__  .exp      : 0.038535295985639095
__main__  .exp      : 11.728486061969306
```

One thing to consider is _what kind_ of time we actually (want to) measure. Time package provides `time.perf_counter` and `time.process_time`. The difference here is that `perf_counter` returns absolute value, which includes time when your Python program process is not running, therefore it might be impacted by machine load. On the other hand `process_time` returns only _user time_ (excluding _system time_), which is only the time of your process.

## Making It Faster

Now, for the fun part. Let's make your Python programs run faster. I'm (mostly) not going to show you some hacks, tricks and code snippets that will magically solve your performance issues. This is more about general ideas and strategies, which when used, can make a huge impact on performance, in some cases up to 30% speed-up.

### Use Built-in Data Types

This one is pretty obvious. Built-in data types are very fast, especially in comparison to our custom types like trees or linked lists. That's mainly because the built-ins are implemented in _C_, which we can't really match in speed when coding in Python.

### Caching/Memoization with `lru_cache`

I already shown this one in previous blog post [here](https://martinheinz.dev/blog/4), but I think it's worth repeating it with simple example:

```
import functools
import time

# caching up to 12 different results
@functools.lru_cache(maxsize=12)
def slow_func(x):
    time.sleep(2)  # Simulate long computation
    return x

slow_func(1)  # ... waiting for 2 sec before getting result
slow_func(1)  # already cached - result returned instantaneously!

slow_func(3)  # ... waiting for 2 sec before getting result
```

The function above simulates heavy computation using `time.sleep`. When called first time with parameter `1`, it waits for 2 seconds and only then returns result. When called again, the result is already cached so it skips body of function and returns result immediately. For more _real life_ example see previous blog post [here](https://martinheinz.dev/blog/4).

### Use Local Variables

This has to do with speed of lookup of variables in each scope. I'm writing _each scope_, because it's not just about using local vs. global variables. There's actually difference in speed of lookup even between - let's say - local variable in function (fastest), class-level attribute (e.g. `self.name` - slower) and global for example imported function like `time.time` (slowest).

You can improve performance, by using seemingly unnecessary (straight-up useless) assignments like this:

```
#  Example #1
class FastClass:

    def do_stuff(self):
        temp = self.value  # this speeds up lookup in loop
        for i in range(10000):
            ...  # Do something with `temp` here

#  Example #2
import random

def fast_function():
    r = random.random
    for i in range(10000):
        print(r())  # calling `r()` here, is faster than global random.random()
```

### Use Functions

This might seem counter intuitive, as calling function will put more stuff onto stack and create overhead from function returns, but it relates to previous point. If you just put your whole code into one file without putting it into function, it will be much slower because of global variables. Therefore you can speed up your code just by wrapping whole code in `main` function and calling it once, like so:

```
def main():
    ...  # All your previously global code

main()
```

### Don't Access Attributes

Another thing that might slow down your programs is _dot operator_ (`.`) which is used when accessing object attributes. This operator triggers dictionary lookup using `__getattribute__`, which creates extra overhead in your code. So, how can we actually avoid (limit) using it?

```
#  Slow:
import re

def slow_func():
    for i in range(10000):
        re.findall(regex, line)  # Slow!

#  Fast:
from re import findall

def fast_func():
    for i in range(10000):
        findall(regex, line)  # Faster!
```

### Beware of Strings

Operations on strings can get quite slow when ran in loop using for example _modulus_ (`%s`) or `.format()`. What better options do we have? Based on recent [tweet from Raymond Hettinger](https://twitter.com/raymondh/status/1205969258800275456), the only thing we should be using is _f-string_, it's most readable, concise AND the fastest method. So, based on that tweet, this is the list of methods you can use - fastest to slowest:

```
f'{s} {t}'  # Fast!
s + '  ' + t
' '.join((s, t))
'%s %s' % (s, t)
'{} {}'.format(s, t)
Template('$s $t').substitute(s=s, t=t)  # Slow!
```

### Generators Can Be Fast

Generators are not inherently faster as they were made to allow for lazy computation, which saves memory rather than time. However, the saved memory can be cause for your program to actually run faster. How? Well, if you have large dataset and you don't use generators (iterators), then the data might overflow CPUs _L1 cache_, which will slow down lookup of values in memory significantly.

When it comes to performance, it's very import that CPU can save all the data it's working on, as close as possible, which is in the cache. You can watch [Raymond Hettingers talk](https://www.youtube.com/watch?v=OSGv2VnC0go&t=8m17s), where he mentions this issues.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjM5MDc4OTBdfQ==
-->