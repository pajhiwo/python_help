
# Data Types

Objects whose value can change are said to be mutable
Objects whose value cannot change are said to be immutable.
Immutable objects are thread safe

## Tuple
Immutable, sequenced, cannot be changed after creation
```python
tup = (1, ‘rtg’, 3)
```

## List
Mutable, sequenced
```python
list = [1, ‘rtg’, 3]
```

## Dictionary
Mutable, not sequenced, slow, keys must be unique
```python
dict = {“key1”: “value”, “key2”: “value”}
```

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

## ByteArray
Mutable array

## Ordered dictionary
collections.OrderedDict

*since Python3.7 builtin dict keeps insertion order*
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
for i, x in enumerate(a): or for k, v in m.iteritems():
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
a = [[1, 2], [3, 4], [5, 6]]

list(itertools.chain.from_iterable(a))
>>> [1, 2, 3, 4, 5, 6]

sum(a, [])
>>> [1, 2, 3, 4, 5, 6]

[x for l in a for x in l]
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
  


<!--stackedit_data:
eyJoaXN0b3J5IjpbNjAyMjkxNjQwXX0=
-->