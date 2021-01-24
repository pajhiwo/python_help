
# Data Types

Objects whose value can change are said to be mutable
Objects whose value cannot change are said to be immutable.
Immutable objects are thread safe

## Tuple
Immutable, sequenced, cannot be changed after creation
```python
tup = (1, ‘rtg’, 3)
```

### Tuple unpacking
```python
mylist =  [(1,2),(3,4),(5,6),(7,8)]
for a,b in mylist:
	print  (a,b)
	print a
	print b
```

### Named tuple
```python
from collections import namedtuple  

City = namedtuple("City", "population area country")  
warsaw = City(1000000, 100, "Poland")  
print(warsaw.population)
```

## List
Mutable, sequenced
```python
list = [1, ‘rtg’, 3]
```

### List Comprehensions
Creating new list in one line
```python
new_list =  [expression(i)  for i in old_list if filter(i)]
```

### += operator
Implementation of `+=` is defined by the class that implements it. That is, to define `+=` the `list` class has defined a `object.__iadd__(self, other)` magic method. And the way it works is the same as `list.extends`.
```python
```
In [25]: lst = [3, 4, 5, 6, 7]

In [26]: lst_copy = lst

In [27]: lst += [8, 9]

In [28]: lst
Out[28]: [3, 4, 5, 6, 7, 8, 9]

In [29]: lst_copy
Out[29]: [3, 4, 5, 6, 7, 8, 9]
```
```

## Dictionary
Mutable, not sequenced, slow, keys must be unique
***since Python3.7 builtin dict keeps insertion order***
```python
dict = {“key1”: “value”, “key2”: “value”}
```
Python dictionaries are implemented as **hash tables**. It is an array whose indexes are obtained using a hash function on the keys. Python hash table is just a contiguous block of memory. **Each slot in the table can store one and only one entry.** Each **entry** in the table actually a combination of the three values: **< hash, key, value >**.

## Set
Mutable, unordered collection of items. Every element is unique (no duplicates) and must be immutable.
```python
A = {1, 2, 3, 3}
>>> set([1, 2, 3])
B = {3, 4, 5, 6, 7}
A | B
>>> set([1, 2, 3, 4, 5, 6, 7])
```
- Set without duplicates
done by 2 sets ->  is done by `|` --> `Set1 | Set2`
  
- Set with only duplicates
done by 2 sets ->  is done by `&` --> `Set1 & Set2`
  
## Sequences    
It is ordered set - organized by non negative indexes: String, List, Tuple, Dict, Set, byteArray

  
## String
Immutable type
**Python 3.8**
F-strings now support = for easy debbuging

## Array
Arrays can hold only a **single data type** elements whereas lists can hold any data type elements.
```python
import array as arr
my_Array = arr.array( 'i',[1, 2, 3, 4])
```

## ByteArray
Mutable array

## Ordered dictionary
collections.OrderedDict

***since Python3.7 builtin dict keeps insertion order***
<br/>

# List methods

## List reverse
```python
list.reverse()
list[::-1]
```

## List last element
```python
list[-1]
```
  
## List slice
a[start:end]
```python
lista[2:8] #from index 2 to 8
```
  
## List slices with step
a[start: end :step]
```python
a[2:8:2]
a[::2] #every second
```
  
## Enumerate 
Function you can iterate through the sequence and retrieve the index position and its corresponding value at the same time.
```python
for i,v in enumerate([‘Python’,’Java’,’C++’]):
    print(i,v)

>>> 0 Python
>>> 1 Java
>>> 2 C++
```
  
## Enumerate / Iterating over list index and value pairs:
```python
a = ['Hello', 'world', '!']
for i, x in enumerate(a): --or-- for k, v in m.iteritems():
    print '{}: {}'.format(i, x)

>>> 0: Hello
>>> 1: world
```
  
## Iterate through more than one list
```python
for i,j in zip(names,emails):
```

## Zipping and unzipping
Two list in a list of tuples
```python 
a = [1, 2, 3]
b = ['a', 'b', 'c']
z = zip(a, b)
>>> [(1, 'a'), (2, 'b'), (3, 'c')]
```

## Flattening lists:
```python    
nested_list = [[1, 2], [3, 4], [5, 6]]

list(itertools.chain.from_iterable(nested_list))
>>> [1, 2, 3, 4, 5, 6]

sum(nested_list, [])
>>> [1, 2, 3, 4, 5, 6]

[item for sublist in nested_list for item in sublist]
>>> [1, 2, 3, 4, 5, 6]
```
  
## Print(”string”[3:5])
prints letters from 3 to 5, but without index 5

## Append() and extend() methods   
append - adds its argument as a single element to the end of a list. The length will increase by one.

extend - iterates over its argument adding each element to the list, extending the list.
 
## 3d array slice
```python
Array[0:2,2:4] 
```
3d array, select rows 0,1 and columns 2,3

## Iterate 2d array
```python
for i in array.flat:
    print i
```

## Stack (concatenate) arrays
```python
numpy.hstack((array,array)) 
```
hstack - horizontal, vstack - vertical

## Split array    
```python
hsplit, vsplit(array,2)
```
represent how many arrays will be created

## Unpack argument from list or tuple
to individual arguments use *:
*function_name*(**variable*) - this is not definition, it is execution
Usually goes with (**args*) in definition

Unpacking with _star expression_ always creates list even if the variable receives zero values from unpacking

```python
first, *middle, last = [1, 2, 3, 4, 5]
# first = 1, middle = [2, 3, 4], last = 5

first, second, *rest = [1, 2, 3, 4, 5]
# first = 1, middle = 2, rest = [3, 4, 5]

name, address, *_, email = ["John", "Some Street", "Credit Card Number", "Phone Number", "john@gmail.com"]
# name = "John", address = "Some Street", email = "john@gmail.com"

header_row, *table_rows = open("filename").read().split("\n")
# header_row -> first line
# table_rows -> list of remaining lines
```

## Most frequently occurring element
`Counter` class in `collections` module. Under the hood, `Counter` is just a dictionary that maps items to number of occurrences,
```python
from collections import Counter

cheese = ["gouda", "brie", "feta", "cream cheese", "feta", "cheddar",
          "parmesan", "parmesan", "cheddar", "mozzarella", "cheddar", "gouda",
          "parmesan", "camembert", "emmental", "camembert", "parmesan"]

cheese_count = Counter(cheese)
print(cheese_count.most_common(3))
# Prints: [('parmesan', 4), ('cheddar', 3), ('gouda', 2)]
```

<br/>

# Dict methods

## Inverting a dictionary using zip
```python
m = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

m.items()
>>> [('a', 1), ('c', 3), ('b', 2), ('d', 4)]

zip(m.values(), m.keys())
>>> [(1, 'a'), (3, 'c'), (2, 'b'), (4, 'd')]

mi = dict(zip(m.values(), m.keys()))
mi
>>> {1: 'a', 2: 'b', 3: 'c', 4: 'd'}
```
 
## Inverting dictionary    
```python
{v: k for k, v in m.items()}

>>> {1: 'a', 2: 'b', 3: 'c', 4: 'd'}
```
  
## Dictionary: d.get(<key>)
if key is not found, it will return None, instead of Error


## Iter dictionary
```python
for key,value in dictionary.items():
```
  
  # String Close Match
 To find words similar to some input string using something like [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance), then Python and `difflib` have your back.
```python
import difflib
difflib.get_close_matches('appel', ['ape', 'apple', 'peach', 'puppy'], n=2)
# returns ['apple', 'ape']
```

## Counter dictionary
You can add or remove
```python
from collections import Counter  
  
magazine = list("two times three is not four".split())  
note = list("two times two is four".split())  
  
print(Counter(note) - Counter(magazine))

> Counter({'two': 1})
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNDk4MjQ5NzMsOTQyMTAwNzQwLDExNz
kzNzk5MCwxNTYyMjkyODM1LDEyNDU4ODA1NDksODUzNDk2MDM3
LC0yMDQxMjAyOTEsMTIzMjE5MTU3LDYyODM3NDY4OSwtMTE3Nj
UwNjgwMSwtNDk0MjAyMzI4LDE4MzA0NjgxNjgsLTg2ODEzOTU2
MiwxNjE3ODA4ODY4LDYwMjI5MTY0MF19
-->