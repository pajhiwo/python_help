
# Function, arguments, reference

All parameters in the Python language are passed by reference.
If you pass a mutable object into a method, the method gets a reference to that same object and you can mutate it to your heart's delight, but if you rebind the reference in the method, the outer scope will know nothing about it, and after you're done, the outer reference will still point at the original object.

NOT POSSIBLE FOR INT: https://stackoverflow.com/questions/15148496/passing-an-integer-by-reference-in-python?lq=1

## Parameter passed by reference
```python
def try_to_change_list_contents(the_list):
    print(f"got {the_list}")
    the_list.append('four')
    print(f"changed to {the_list}")

outer_list = ['one', 'two', 'three']
print(f"before, outer_list ={outer_list}")
try_to_change_list_contents(outer_list)
print(f"after, outer_list = {outer_list}")

Output:
>>> before, outer_list = ['one', 'two', 'three']  
>>> got ['one', 'two', 'three']  
>>> changed to ['one', 'two', 'three', 'four']  
>>> after, outer_list = ['one', 'two', 'three', 'four']
```

## Parameter passed by value:

     
```python    
def try_to_change_list_reference(the_list):
    print(f"got {the_list}")
    the_list = ['and', 'we', 'can', 'not', 'lie']
    print(f"set to {the_list}")

outer_list = ['we', 'like', 'proper', 'English']
print(f"before, outer_list = {outer_list}")
try_to_change_list_reference(outer_list)
print(f"after, outer_list = {outer_list}")

Output:
>>> before, outer_list = ['we', 'like', 'proper', 'English']  
>>> got ['we', 'like', 'proper', 'English']  
set to ['and', 'we', 'can', 'not', 'lie']  
>>> after, outer_list = ['we', 'like', 'proper', 'English']
```

## Object reference

```python
some_guy = 'Fred'
first_names = []
first_names.append(some_guy)
another_list_of_names = first_names
```
another_list_of_names is referencing to the same object as first_names, so every change in first_names will be present in another_list_of_names. Both names are simply bound to the same object

## Saving memory by reference
If we create 10 string objects with the same value, every identifier (object) would refer to the same string by reference to the same memory space
```python
ttt = "python"
ttt2 = "python"

print(id(ttt))
>>> 4298242544
print(id(ttt2))
>>> 4298242544
```

## Access (parent) function variable
from nested function use “nonlocal <variable>”
```python
def outer():
    count = 0

        def inner():
            nonlocal count
```

## *args
for passing multiple arguments to a function and stores them in tuple

  
## *kwargs
for passing multiple arguments to a function and stores them in dictionary

  
## lambda
Single expression anonymous function

lambda num: num * num -> <parameters>: <what to do with parameters>

  
## References to names in modules
are attribute references: in the expression modname.funcname, modname is a module object and funcname is an attribute of it

## Unpack tuple, list, dict to function arguments
For tuple, list  use *
```python
function_name(*variable)

def updateStudentDetail(name, phone, address):
    print(f"Student Name: {name}")
    print(f"Student phone: {phone}")
    print(f"Student address: {address}") 

details  =  ["Riti", "3343", "Delhi"]

updateStudentDetail(*details)
>>> Student Name  :  Riti
>>> Student phone  :  3343
>>> Student address  :  3343
```
For dict  use **
```python
function_name(**variable)

def updateStudentDetail(name, phone, address):
    print(f"Student Name: {name}")
    print(f"Student phone: {phone}")
    print(f"Student address: {address}") 

details  =  {'name': 'Sam', 'phone': '112', 'address': 'London'}

updateStudentDetail(**details)
>>> Student Name  :  Sam
>>> Student phone  :  112
>>> Student address  :  London
```
## Function with ONLY keyword arguments
To create function that only takes (force) keyword arguments by placing single `*` argument before keyword arguments.
```python
def test(*, a, b):
 pass

test("value for a", "value for b")  # TypeError: test() takes 0 positional arguments...
test(a="value", b="value 2")  # Works...
```

##
<!--stackedit_data:
eyJwcm9wZXJ0aWVzIjoiY2F0ZWdvcmllczogJ2tleXdvcmQsIH
JlZmVyZW5jZSwgYXJndW1lbnRzLCBhcmdzLCBsYW1iZGEnXG4i
LCJoaXN0b3J5IjpbLTYxMDM5Njg2NSwxMTgwNDY1OTUsMTQxNz
Q4ODAxMl19
-->