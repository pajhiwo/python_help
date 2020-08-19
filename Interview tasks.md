## Palindrome test

```python
def check_palidrome(txt):
	if txt == txt[::-1]:
		return("palindrome")
	else:
		return("not palindrome")
```

## Common letters in two strings
```python
print(set(text1)&set(text2))
```

## Count letters in string
```python
from collections import Counter
counter(Counter(text1))
```

## Print diamond
```python
def print_diamond(n):  
    iter_list = (list(range(1, n)))  
    iter_list.extend((iter_list[2::-1]))  # starting from index 2, reverse  
  for i in iter_list:  
        print("*"*i)
```

## Capitalize every word in sentence
```python
def toJadenCase(string):        
    return " ".join(w.capitalize() for w in string.split())
```

## Group chars by similar char next to each other
```python
example = "AAAABBBCCDAABBB"
def unique_in_order(iterable):  
    output = []  
    for key,group in itertools.groupby(iterable):  
        output.append(key)  
    return(output)
>>>['A', 'B', 'C', 'D', 'A', 'B']
```

## Print phone number:
```python
number = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]  
  
def create_phone_number(n):  
    return "({}{}{}) {}{}{}-{}{}{}{}".format(*n)
```

## Find different odd / even number from list of numbers
```python
def iq_test(numbers):
    e = [int(i) % 2 == 0 for i in numbers.split()]  # --> e = [True, True, False, True, etc]
    return e.index(True) + 1 if e.count(True) == 1 else e.index(False) + 1
```

## Move zeros to end of list
```python
def move_zeros(array):  
    l = [i for i in array if isinstance(i, bool) or i!=0]  
    return l + [0]*(len(array) - len(l))
```

## Optimize Fibonacci by Memoization
```python
def fibonacci(n):  
    cache = {}  
 
    def recurse(num):  
        if num in cache:  
            return cache[num]  
        if num in [0, 1]:  
            return num  
            
        result = recurse(num - 1) + recurse(num - 2)  
        cache[num] = result  
        return result  
    return recurse(n)
```
### Faster methong by using decorator
```python
from functools import lru_cache

@lru_cache(maxsize = 1000)  
def fibonacci(input_value):  
    if input_value in [0, 1]:  
        return input_value  
    else:  
        return fibonacci(input_value - 1) + fibonacci(input_value - 2)
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNTMyNTcxMDYsNjU1MzUyMjk4LDE1Mz
AyMzE0MywtOTI5MDEyMjc1LDIwNTE4MTAxMTMsLTk3NjM0MDMz
NSw1ODg5MTM3NzJdfQ==
-->