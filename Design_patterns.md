# Design patterns

## Singleton
is a software design pattern that restricts the instantiation of a class to one object.

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



* Example 2:
```python
class Singleton(object):
    _instance = None
    def __new__(cls, *args, **kwargs):
        if not cls._instance:
            cls._instance = object.__new__(cls, *args, **kwargs)
        return cls._instance

class Fire(Singleton):
     pass

f1 = Fire()
f2 = Fire()

```
  

Ex3:
```python
class OnlyOne:  
    class __OnlyOne:  
        def __init__(self, arg):  
            self.val = arg  
        def __str__(self):  
            return repr(self) + self.val  
    
    instance = None  
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
eyJoaXN0b3J5IjpbMTIzNTY5NDUxMywtOTgyMzI1NjA3LC0xMz
ExMjczNDU3LC0xMjY3NDc2Njg3LC0xMTk2NDQwMjYxXX0=
-->