# Design patterns

## Singleton
Is a software design pattern that restricts the instantiation of a class to one object.

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
class Singleton(object):
    _instance = None
    def __new__(cls, *args, **kwargs):
        if not cls._instance:
            cls._instance = object.__new__(cls, *args, **kwargs)
        return cls._instance

class Fire(Singleton):
     pass

class Fire(Singleton):  
    def __init__(self):  
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
Factory Method should be used in every situation where an application (client) depends on an interface (product) to perform a task and there are multiple concrete implementations of that interfac

Resources:
[Link](https://python-3-patterns-idioms-test.readthedocs.io/en/latest/Factory.html)
[Link](https://realpython.com/factory-method-python/)

* **Basic example**
```python
class Shape():  
    # Create based on class name  
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
    pass

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


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg3NzY5Njc3MCwxNTM3MTk0NDUyLDk4Mz
Q2Mjk2NiwtMTcyOTU2NjIyOSwtMTA4NDQyNDM5MCwtNDA4Mzg2
MTEzLC0xNzY5NDExNDEsMTQzMzA5OTUyOCw2NzgzOTQ1MTgsMT
gzNDE0MTE4MiwtMTAxNTcyNzg2MiwtOTgyMzI1NjA3LC0xMzEx
MjczNDU3LC0xMjY3NDc2Njg3LC0xMTk2NDQwMjYxXX0=
-->