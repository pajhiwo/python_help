## HackerRank
https://github.com/marinskiy/HackerrankPractice
https://shounaklohokare.medium.com/

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
import itertools

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
[https://towardsdatascience.com/memoization-in-python-57c0a738179a](https://towardsdatascience.com/memoization-in-python-57c0a738179a)
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
### Faster methond by using decorator
```python
from functools import lru_cache

@lru_cache(maxsize = 1000)  
def fibonacci(input_value):  
    if input_value in [0, 1]:  
        return input_value  
    else:  
        return fibonacci(input_value - 1) + fibonacci(input_value - 2)
```

## First non-repeating character
```python
def first_non_repeating_letter(string):
    string_lower = string.lower()
    for i, letter in enumerate(string_lower):
        if string_lower.count(letter) == 1:
            return string[i]
            
    return ""
```

## Words to number
```python
def parse_int(string):  
    units = ["zero", "one", "two", "three", "four", "five", "six", "seven", "eight",  
  "nine", "ten", "eleven", "twelve", "thirteen", "fourteen", "fifteen",  
  "sixteen", "seventeen", "eighteen", "nineteen",]  
  
    tens = ["", "", "twenty", "thirty", "forty", "fifty", "sixty", "seventy", "eighty", "ninety"]  
  
    hundreds = ["hundred", "thousand", "million", "billion", "trillion"]  
  
    current = result = 0  
    for word in string.replace(" and", "").replace("-", " ").split():  
        if word in units:  
            num = units.index(word)  
        elif word in tens:  
            num = tens.index(word) * 10  
        elif word in hundreds:  
            idx = hundreds.index(word)  
            num = 10 ** (idx * 3 or 2)  
  
       
        if num < 100:  
            current += num  
        elif num == 100:  
            current = current * num  
        elif num > 100:  
            result += current * num  
            current = 0  
  return result + current
```

## Binary tree



```python

class Node(object):
	def __init__(self, d):
		self.data = d
		self.left = None
		self.right = None
		
	def insert(self, d):
		if self.data == d:
			return False
		elif d < self.data:
			if self.left:
				return self.left.insert(d)
			else:
				self.left = Node(d)
				return True
		else:
			if self.right:
				return self.right.insert(d)
			else:
				self.right = Node(d)
				return True
				
	def find(self, d):
		if self.data == d:
			return True
		elif d < self.data and self.left:
			return self.left.find(d)
		elif d > self.data and self.right:
			return self.right.find(d)
		return False

```


## Count sum of infinite list
```python
n(n+1)/2
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMwOTA5Nzg2MSwtMTExOTAyMjUxNywtMT
k1MDI3NDMxMywxNDAxNzE0ODY0LDU3MTU2NTA4NSw5OTk4Nzc2
NjMsMTM0MTQyMTI0MiwtMTAyODM1NTU2NiwtMTY0NjQwMTUxOC
wtMTE4MjA3NDc5NV19
-->