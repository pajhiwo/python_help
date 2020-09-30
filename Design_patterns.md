# Design patterns
Resources:
[Link](https://www.tutorialspoint.com/python_design_patterns/python_design_patterns_adapter.htm)
[Link](https://refactoring.guru/design-patterns/python)

## Singleton
Is a software design pattern that restricts the instantiation of a class to one object.

Resources:
[Link](https://stackoverflow.com/questions/6760685/creating-a-singleton-in-python)
[Link]([https://xiaoxing.us/2018/04/15/singleton-in-python/])
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
Possibility to reset instance/create new one via `_reset_instance`
```python
class Singleton(type):  
    _instances = {}  
  
    def __call__(cls, *args, **kwargs):  
        if cls not in cls._instances:  
            cls._instances[cls] = super(Singleton, cls).__call__(*args, **kwargs)  
        return cls._instances[cls]

    @staticmethod  
    def  _reset_instance():
	    # erase existing instances  
	    for instance in Singleton._instances:
		    del instance 
		Singleton._instances =  {}
    
  
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
* **Module**
Modules are imported only once. If using `from singmodule import *` it will only allow to import what is specified in `__all__`. 
```python
# singmodule.py
class Foo(object):
     pass

global_variable = Foo()  
  
__all__ = ["global_variable"]
```
Alternatively you can have only methods and variables (without class) on "module.py" and then import such module.

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

>>> Object created: <__main__.Singleton object at 0x7f59442d58d0>
>>> Object created: <__main__.Singleton object at 0x7f59442d58d0>
```  
## Borg "singleton"
Borg is also known as **monostate**. In the borg pattern, all of the instances are different, but they share the same

```python
class Borg:
    __shared_state = {}
    def __init__(self):
        self.__dict__ = self.__shared_state
    # and whatever else you want in your class -- that's all!

if _ _name_ _ == '_ _main_ _':
    class Example(Borg):
        def _ _init_ _(self, name=None):
            Borg._ _init_ _(self)
            if name is not None: self.name = name
        def _ _str_ _(self): return 'Example(%s)' % self.name
    a = Example('Lara')
    b = Example(  )
    print a, b
    c = Example('Boris')
    print a, b, c
    b.name = 'Marcel'
    print a, b, c

>>>
**Example(Lara) Example(Lara)**
**Example(Boris) Example(Boris) Example(Boris)**
**Example(Marcel) Example(Marcel) Example(Marcel)**
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


## Adapter pattern
Converts interface of a class into another. 

```python
# (via object composition)
class Target():
	"""
	The Target defines the domain-specific interface used by the client code.
	"""

    def request(self) -> str:
        return "Target: The default target's behavior."

class Adaptee:
	"""
	The Adaptee contains some useful behavior, but its interface is incompatible
	with the existing client code. The Adaptee needs some adaptation before the
	client code can use it.
	"""

    def specific_request(self) -> str:
        return ".eetpadA eht fo roivaheb laicepS"

class Adapter(Target):
	"""
	The Adapter makes the Adaptee's interface compatible with the Target's
	interface.
	"""

    def __init__(self, adaptee: Adaptee) -> None:
        self.adaptee = adaptee

    def request(self) -> str:
        return f"Adapter: (TRANSLATED) {self.adaptee.specific_request()[::-1]}"

def client_code(target: Target) -> None:
	"""
	The client code supports all classes that follow the Target interface.
	"""

    print(target.request(), end="")

if __name__ == "__main__":
    print("Client: I can work just fine with the Target objects:")
    target = Target()
    client_code(target)
    print("\n")

    adaptee = Adaptee()
    print("Client: The Adaptee class has a weird interface. See, I don't understand it:")
    print(f"Adaptee: {adaptee.specific_request()}", end="\n\n")

    print("Client: But I can work with it via the Adapter:")
    adapter = Adapter(adaptee)
    client_code(adapter)
```

## Abstract pattern

## Policy-based design

## Page object

## Policy-based design




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3Nzk4NjcxOTAsNzg3NzE2NzMxLDczMz
Y1MzQ5NywzNjE0MDY1ODIsODc4Mjg1NTYzLDY1MTg0MzkxLDEw
ODQ4MjkyNDksMTkzNjMwNDcsMTQyMTQzMDQ3MCwxMTkwNzY3OT
Q3LDc3ODAzMjI2MywxMTcyODMwODc1LC0xMDc3OTk1NTUxLDIw
MTYzMTgwNzcsLTEzNjcyMDAzMTAsLTEwMDg3NTQ2ODcsMTUyOD
IwMDk5OSwtNjg5MTAzODkyLC0xNDYzMTEwMTM0LDEyNDA2ODcw
OF19
-->