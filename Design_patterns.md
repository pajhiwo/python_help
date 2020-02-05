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
Is a creation methods, which create objects from concrete classes, but return them as objects of abstract type or interface (class to create different types of objects).
Forces the creation of objects to occur through a common _factory_ class.
* **Basic example**
```python
class Shape():  
    # Create based on class name:  
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

* Preventing direct creation

## Policy-based design

## Page object pattern

## Abstract pattern


<!--stackedit_data:
eyJoaXN0b3J5IjpbNjI1MTM3NDk3LC00MDgzODYxMTMsLTE3Nj
k0MTE0MSwxNDMzMDk5NTI4LDY3ODM5NDUxOCwxODM0MTQxMTgy
LC0xMDE1NzI3ODYyLC05ODIzMjU2MDcsLTEzMTEyNzM0NTcsLT
EyNjc0NzY2ODcsLTExOTY0NDAyNjFdfQ==
-->