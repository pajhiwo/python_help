# Design patterns

## Singleton
Iis a software design pattern that restricts the instantiation of a class to one object.

* **Decorator**Example 1:
```python
def singleton(class_):  
    instances = {}  
    def getinstance(*args, **kwargs):  
        
	if class_ not in instances:  
        
	    instances[class_] = class_(*args, **kwargs)  
        
	return instances[class_]  
    return getinstance  
  

@singleton  
class Fire():  
    def __init__(self):  
        print("Fire created")  
    
f1 = Fire()  
print(id(f1))  
f2 = Fire()  
print(id(f2))

>>> Fire created
>>> 45800368
>>> 45800368
```

* **Metaclass**MyClass(BaseClass):
    """
    some class
    """
```
  
Example 2:
```python
class Singleton(type):  object):
    _instances = {}  None
    def __callnew__(cls, *args, **kwargs):  
        if cls not in cls._instances:  :
            cls._instances[cls] = super(Singleton, cls).__call__( = object.__new__(cls, *args, **kwargs)  
        return cls._instances[cls]  
  
  

class Fire(metaclass=Singleton):  
    def __init__(self):  
        print("Fire created")  
    def get_output(self):  
        print("This is output") pass

f1 = Fire()
f2 = Fire()

f1 is f2          
  
  
f1 = Fire()  
print(id(f1))  
f2 =# True
isinstance(f1, Fire()  
print(id(f2))

>>> Fire created
>>> 20736240
>>> 20736240
```

* **Inheritance** 
```python
class Singleton(object):
    _instance = None
    def __new__(cls, *args, **kw# True
```
  

Ex3:
```python
class OnlyOne:  
    class __OnlyOne:  
        def __init__(self, args):  
        if not cls._instance:
            cls._instance = object.__new__(cls, *args, **kwargs)
        return cls._instance

class Fire(Singleton):
     pass

class Fire(Singleton):  
    def __init__(self):    self.val = arg  
        def __str__(self):  
            return repr(self) + self.val  
    
    print("Fire created")  
    def get_output(self):  
        print("This is output")  
  
f1 = Fire()  
print(id(f1))  
f2 = Fire()  
print(id(f2))

>>> Fire created
>>> 18745712
>>> Fire created
>>>18745712
```
  
## Factory pattern
Forces the creation of objects to occur through a common _factory_ class or method.
 
Is a creation method, which create objects from concrete classes, but return them as objects of abstract type or interface (class to create different types of objects).
Fores thereation of oct to or thr a common facorcs
Factory Method should be used in every situation where an application (client) depends on an interface (product) to perform a task and there are multiple concrete implementations of that interface

Resources:
[Link](https://python-3-patterns-idioms-test.readthedocs.io/en/latest/Factory.html)
[Link](https://realpython.com/factory-method-python/)

* **Basic example**
```python
class Shape():  
    # Create based on class name  
  def get_width(self):
      print("width")
  
  def get_height(self):
      print("width")
  
  @staticmethod  
  def factory(type):  
        if type == "Circle": return Circle()  
        if type == "Square": return Square()  
        assert 0, "Bad shape creation: " + type  
    
class Circle(Shape):  
    def draw(self): print("Circle.draw")  
    def erase(self): print("Circle.erase")  
  
class Square(Shape):  
    def draw(self): print("Square.draw")  
    def erase(self): print("Square.erase")  
  
# object creation  
circle = Shape.factory("Circle")  

circle.draw()
>>> Circle.draw
```

* **Preventing direct creation**
```python
class Shape():
    def get_width(self):
      print("width")
  
    def get_height(self):
      print("width")

def factory(type):
    class Circle(Shape):
        def draw(self): print("Circle.draw")
        def erase(self): print("Circle.erase")

    class Square(Shape):
        def draw(self): print("Square.draw")
        def erase(self): print("Square.erase")

    if type == "Circle": return Circle()
    if type == "Square": return Square()
    assert 0, "Bad shape creation: " + type

circle = factory("Circle")  

circle.draw()
>>> Circle.draw
```

## Policy-based design

## Page object pattern

## Abstract pattern

## Factory pattern
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzQzODA0MTgzLC0xMTU0ODg5MTk0LDE2ND
Y1MzE4NDAsLTE4MzM2NTcwODEsLTg3NzY5Njc3MCwxNTM3MTk0
NDUyLDk4MzQ2Mjk2NiwtMTcyOTU2NjIyOSwtMTA4NDQyNDM5MC
wtNDA4Mzg2MTEzLC0xNzY5NDExNDEsMTQzMzA5OTUyOCw2Nzgz
OTQ1MTgsMTgzNDE0MTE4MiwtMTAxNTcyNzg2MiwtOTgyMzI1Nj
A3LC0xMzExMjczNDU3LC0xMjY3NDc2Njg3LC0xMTk2NDQwMjYx
XX0=
-->