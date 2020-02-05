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
Factory Method should be used in every situation where an application (client) depends on an interface (product) to perform a task and there are multiple concrete implementations of that interfac

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
>>> Circle.drawinstance = None  
    def __init__(self, arg):  
        if not OnlyOne.instance:  
            OnlyOne.instance = OnlyOne.__OnlyOne(arg)
        else:  
            OnlyOne.instance.val = arg  
    def __getattr__(self, name):  
        return getattr(self.instance, name)  
  
x = OnlyOne('sausage')  
print(x)  
y = OnlyOne('eggs')  
print(y)  
z = OnlyOne('spam')  
print(z)  
print(x)  
print(y)  
print(`x`)  
print(`y`)  
print(`z`)  
output = '''  
<__main__.__OnlyOne instance at 0076B7AC>sausage  
<__main__.__OnlyOne instance at 0076B7AC>eggs  
<__main__.__OnlyOne instance at 0076B7AC>spam  
<__main__.__OnlyOne instance at 0076B7AC>spam  
<__main__.__OnlyOne instance at 0076B7AC>spam  
<__main__.OnlyOne instance at 0076C54C>  
<__main__.OnlyOne instance at 0076DAAC>  
<__main__.OnlyOne instance at 0076AA3C>
```

## Policy-based design

## Page object pattern

## Abstract pattern

## Factory pattern
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAxNjQwNDEyOCwtMTgzMzY1NzA4MSwtOD
c3Njk2NzcwLDE1MzcxOTQ0NTIsOTgzNDYyOTY2LC0xNzI5NTY2
MjI5LC0xMDg0NDI0MzkwLC00MDgzODYxMTMsLTE3Njk0MTE0MS
wxNDMzMDk5NTI4LDY3ODM5NDUxOCwxODM0MTQxMTgyLC0xMDE1
NzI3ODYyLC05ODIzMjU2MDcsLTEzMTEyNzM0NTcsLTEyNjc0Nz
Y2ODcsLTExOTY0NDAyNjFdfQ==
-->