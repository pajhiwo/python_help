# Design patterns

## Singleton
is a software design pattern that restricts the instantiation of a class to one object.
Example 1:
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
>>> Fire created

f2 = Fire()
>>>>
```
  
Example 2:
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

f1 is f2              # True
isinstance(f1, Fire)  # True
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
eyJoaXN0b3J5IjpbLTEyNjc0NzY2ODcsLTExOTY0NDAyNjFdfQ
==
-->