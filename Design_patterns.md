# Design patterns

## Singleton
is a software design pattern that restricts the instantiation of a class to one object.

```python

def singleton(class_):
	instances = {}
	def getinstance(*args, **kwargs):
		if class_ not in instances:instances[class_] = class_(*args, **kwargs)

return instances[class_]

return getinstance

  

@singleton

class MyClass(BaseClass):

Pass
```
  

Ex2:

class  Singleton:  
""" A python singleton """  
  
class  __impl:  
""" Implementation of the singleton interface """  
  
def  spam(self):  
""" Test method, return singleton id """  
return  id(self)  
  
# storage for the instance reference  
__instance  =  None  
  
def  __init__(self):  
""" Create singleton instance """  
# Check whether we already have an instance  
if  Singleton.__instance  is  None:  
# Create and remember instance  
Singleton.__instance  =  Singleton.__impl()  
  
# Store instance reference as the only member in the handle  
self.__dict__['_Singleton__instance']  =  Singleton.__instance  
  
def  __getattr__(self,  attr):  
""" Delegate access to implementation """  
return  getattr(self.__instance,  attr)  
  
def  __setattr__(self,  attr,  value):  
""" Delegate access to implementation """  
return  setattr(self.__instance,  attr,  value)  
  
  
# Test it  
s1  =  Singleton()  
print  id(s1),  s1.spam()  
  
s2  =  Singleton()  
print  id(s2),  s2.spam()  
  
# Sample output, the second (inner) id is constant:  
# 8172684 8176268  
# 8168588 8176268

  

Ex3:

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
## Policy-based design

## Page object pattern

## Abstract pattern

## Factory pattern
<!--stackedit_data:
eyJoaXN0b3J5IjpbODQ2OTM2NDAzXX0=
-->