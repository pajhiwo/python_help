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
  
## Package
Collection of Python modules

You can think of packages as the directories on a file system and modules as files within directories.

Any module that contains a `__path__` attribute is considered a package.

Regular package is typically implemented as a directory containing an `__init__.py` file.
  
## Module    
Single Python file.
  
## Expressions
`foo = "hello"` is a statement that assigns foo to the value of the expression "hello"

## Limit import
We can limit what can be imported when using `__all__`
```python
def foo():
 pass

def bar():
 pass

__all__ = ["bar"]
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg4MDEzMDE2Ml19
-->