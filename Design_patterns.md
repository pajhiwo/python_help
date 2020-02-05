# Design patterns

## Singleton
Is a software design pattern that restricts the instantiation of a class to one object.

Resources:
[Link](https://stackoverflow.com/questions/6760685/creating-a-singleton-in-python)
* **Decorator**
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

* **Metaclass**

```python
class Singleton(type):  
    _instances = {}  
  
    def __call__(cls, *args, **kwargs):  
        if cls not in cls._instances:  
            cls._instances[cls] = super(Singleton, cls).__call__(*args, **kwargs)  
        return cls._instances[cls]  
  
class Fire(metaclass=Singleton):  
    def __init__(self):  
        print("Fire created")  
  
    def get_output(self):  
        print("This is output")  
        pass  
  
f1 = Fire()  
print(id(f1))  
f2 = Fire()  
print(id(f2))

>>> Fire created
>>> 20736240
>>> 20736240
```

* **Inheritance** 
```python
class Singleton():  
    _instance = None  
 def __new__(class_, *args, **kwargs):  
        if not isinstance(class_._instance, class_):  
            class_._instance = object.__new__(class_, *args, **kwargs)  
        return class_._instance

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
>>> 18745712
```

* **Overwrite `__new__`** 
```python
class Singleton:
    def __new__(self):
        if  not  hasattr(self, 'instance'):
            self.instance = super().__new__(self)
        return  self.instance

  

s = Singleton()

print("Object created:", s)

  

s1 = Singleton()

print("Object created:", s1)
```  

## Factory pattern
Forces the creation of objects to occur through a common _factory_ class or method.
 
Is a creation method, which create objects from concrete classes, but return them as objects of abstract type or interface (class to create different types of objects).

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
eyJoaXN0b3J5IjpbLTIwOTkxNzI0NjMsLTY4OTEwMzg5MiwtMT
Q2MzExMDEzNCwxMjQwNjg3MDgsLTU1NTU4OTc4LC05MjQ5Njg3
MzQsODczMzI1ODgxLC0xMTU0ODg5MTk0LDE2NDY1MzE4NDAsLT
E4MzM2NTcwODEsLTg3NzY5Njc3MCwxNTM3MTk0NDUyLDk4MzQ2
Mjk2NiwtMTcyOTU2NjIyOSwtMTA4NDQyNDM5MCwtNDA4Mzg2MT
EzLC0xNzY5NDExNDEsMTQzMzA5OTUyOCw2NzgzOTQ1MTgsMTgz
NDE0MTE4Ml19
-->