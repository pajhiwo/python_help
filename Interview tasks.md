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


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NzM4MDUyNzEsLTkyOTAxMjI3NSwyMD
UxODEwMTEzLC05NzYzNDAzMzUsNTg4OTEzNzcyXX0=
-->