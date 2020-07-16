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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA1MTgxMDExMywtOTc2MzQwMzM1LDU4OD
kxMzc3Ml19
-->