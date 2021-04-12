

# Iterators and Generators

## Iterator
iter()” takes an iterable object and returns an iterator. Iterator object can be used only once. It means after it raises StopIteration once, it will keep raising the same exception.
In creating an iterator in python, we use the iter() and next() functions
```python
x = iter([1, 2, 3])
x
>>> <listiterator object at 0x1004ca850>

next(x)
>>> 1

next(x)
>>> 2
```
  

## Generator
Generators simplifies creation of iterators. Generator is a function that produces a sequence of results instead of a single value. When next method is called for the first time, the function starts executing until it reaches yield statement. The yielded value is returned by the next call (next iteration).
Every generator is an iterator, but not vice versa

```python
def yrange(n):
    i = 0
    while i < n:
        yield i
        i += 1
```
```python

x = (i for i in range(0))
type(x)

>>> generator

```
  

## Range
    
Range in python 3 is a generator
```python
generatorsobj = (i**i for i in range(1, 5))

print(next(generatorsobj))
>>> 1

print(next(generatorsobj))
>>> 4
```

<br/>

## Iterator class
```python
class Product:
	def __init__(self, name, price):
		self.name = name
		self.price = price

	def __str__(self):
		return f"Product: {self.name}, ${self.price:.2f}"

	def __iter__(self):
		self._free_samples = [Product(self.name, 0) for _ in range(3)]
		print("Iterator of the product is created.")
		return self

	def __next__(self):
		if self._free_samples:
			return self._free_samples.pop()
		else:
			raise StopIteration("All free samples have been dispensed.")

product = Product("Perfume", 5.0)
for i, sample in enumerate(product, 1):
	print(f"Dispense the next sample #{i}: {sample}")
>>>
Iterator of the product is created.
Dispense the next sample #1: Product: Perfume, $0.00
Dispense the next sample #2: Product: Perfume, $0.00
Dispense the next sample #3: Product: Perfume, $0.00
```

# Context managers

Way of dealing with opening resources like opening files. Using with, we can call anything that returns a context manager (like the built-in open() function). Variable only exists within the indented block below the with statement

`with something_that_returns_a_context_manager() as my_resource:  
do_something(my_resource)`

 
The simplest is to define a class that contains two special methods: `__enter__()` and `__exit__()`
```python
class File():
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
    
    def __enter__(self):
        self.open_file = open(self.filename, self.mode)
    return self.open_file

    def __exit__(self, *args):
        self.open_file.close()

files = []

for _ in range(10000):
    with File('foo.txt', 'w') as infile:
        infile.write('foo')
        files.append(infile)
``` 
Decorator + generator can also be created as context manager. Everything before the
call to yield is considered the code for `__enter__()`. Everything after is the code for `__exit__()`:
```python
from contextlib import contextmanager

@contextmanager
def open_file(path, mode):
    the_file = open(path, mode)
    yield the_file
    the_file.close()
```

## Spread operator
If you apply `*(...)` a.k.a. the _spread_ operator to the iterable, each item in the iterable is treated as an argument of the outer function call (`product`).
```python
print(range(5))
>>> range(0, 5)

print(*range(5))
>>> 0 1 2 3 4
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQxNzMxNTMxNCwxNjkzMzQ2NzU2LC03MD
M3MzMxNjgsMTQ3Mjg2NjMwOSwtNDIzMDQwNjgyLDUzMzQ1NDI3
MSwtMjAxNjg2NjE0MV19
-->