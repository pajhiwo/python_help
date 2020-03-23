# Other

## split(), sub(), subn() methods of “re”
`split()` – uses a regex pattern to “split” a given string into a list.

`sub()` – finds all substrings where the regex pattern matches and then replace them with a different string

`subn()` – it is similar to sub() and also returns the new string along with the no. of

  
## Inline statement    
`print("Positive" if a>0 else "Negative")` has to have else
  
## == vs is    
-  `==` check for value
-  `is` check if both has the same place in memory, different objects
    
## //    
is division showing only digits before decimal

- `//` gives you int 
- `/` gives you float

## [::]    
makes a copy of a list, not reference
  
##  `**`
`a**b` -> a raised to power of b

## dir(object)
list available functions, for built-in method: `dir(__builtins )`
  
## help(object)    
display object documentation

## file.seek(0)    
move file pointer back to beginning of the file (index)

## string.rstrip()    
Returns a copy of the string in which all chars have been stripped from the end of the string
  
## id()   
This function returns the unique identity of an object
`id(x)` is the memory address where x is stored
  
## Module    
Single Python file.

## Package
Collection of Python modules

You can think of packages as the directories on a file system and modules as files within directories.

Any module that contains a `__path__` attribute is considered a package.

Regular package is typically implemented as a directory containing an `__init__.py` file.
  
  
## Expressions
`foo = "hello"` is a statement that assigns foo to the value of the expression "hello"

## Limit import
We can limit what can be imported when using `from some_module import *`. For this specific example, _wildcard import_ with only import `bar`
```python
def foo():
 pass

def bar():
 pass

__all__ = ["bar"]
```

## IP Address
```python
import ipaddress
net = ipaddress.ip_network('74.125.227.0/29')  # Works for IPv6 too
# IPv4Network('74.125.227.0/29')

for addr in net:
    print(addr)

# 74.125.227.0
# 74.125.227.1
# 74.125.227.2
# 74.125.227.3
# ...
```

```python
ip = ipaddress.ip_address("74.125.227.3")

ip in net
# True

ip = ipaddress.ip_address("74.125.227.12")
ip in net
# False
```
## Variable annotation
Seeting type for variable
[Link](https://www.python.org/dev/peps/pep-0526/#id4)
```python
from typing import List
primes: List[int] = []
```

## Serialization
**Pickle** module accepts any Python object and converts it into a string representation and dumps it into a file
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MjUxMDc5ODIsLTEyMjAxNTI1ODQsMT
YzMzUyODAwMSwtMTU4MjE0ODc0NSwtNDM3NTM1NSw1MDMwMTM5
NjVdfQ==
-->