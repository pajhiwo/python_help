# Classes

## Protected member in a Python class
    

All the members of a class in Python are public by default. You don’t need to define an access specifier for members of the class. By adding ‘_’ as a prefix to the member of a class, by convention you are telling others please don’t use this object, if you are not a subclass the respective class.

  ## Class variable vs instance variable
```python
 class Adventure:
	 equipment = ['axe', 'potion']  # class variable
	 
	 def __init__(self, name):
		 self.name = name			# instance variable
```

## self
    

parameter is a reference to the class itself, and is used to access variables that belongs to the class.
```python
class TestClass:
    x = 5
    def __init__(self):
        self.x = self.x+1
  
testObj = TestClass()

print(testObj.x)
>>> 6
```  

But:
```python
class TestClass:
    x = 5
    def __init__(self):
        x=self.x+1

testObj = TestClass()

print(testObj.x)
>>> 5
```

## Modify class parameter
    
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def myfunc(self):
        print("Hello my name is " + self.name)

p1 = Person("John", 36)

print(p1.age)
>>> 36

p1.age = 40

print(p1.age)
>>> 40
```

## Bound methods
Instance methods can be bound via a dotted lookup for use later.
```python
join_with_colons = ':'.join

print(join_with_colons('abcde'))
>>> 'a:b:c:d:e'
```
  
## @staticmethod
Static method is a method that is bound to a class not its object.

Don’t have access to cls or self, doesn’t know class or instance it was called on.

Static method definition is immutable via inheritance.
```python
class A(object):
    def __init__(self):
        self.ttt = "init_var"
    
    def foo(self, x):
        print(f"executing foo {self}, {x}")

    @classmethod
    def class_foo(cls, x):
        print(f"executing class_foo {cls}, {x}")

    @staticmethod
    def static_foo(x):
        print(f"executing static_foo {x}")
        print(self.XXX ) → # >>> Error no access to self 

a = A()

a.static_foo(1)
>>> executing static_foo 1

A.static_foo('hi')
>>> executing static_foo hi
```
  
## @classmethod    
Class method is bound to a class not its object.

Can’t access the class instance (self), can access the class (cls - implicit parameter).

Knows class it was called on, belong to the class’s namespace.

Can be used to create alternative constructors - factory methods - methods which return a class object.

```python
class A(object):
    def __init__(self):
    self.ttt = "init_var"

    def foo(self, x):
    print(f"executing foo {self}, {x}")

    @classmethod
    def class_foo(cls, x):
        print(f"executing class_foo {cls}, {x}")

    @staticmethod
    def static_foo(x):
        print(f"executing static_foo {x}")
  
a = A()

a.class_foo(1)
>>> executing class_foo <class '__main__.A'>, 1

A.class_foo(1)
>>> executing class_foo <class '__main__.A'>, 1

A.foo(1)
>>> TypeError
```
  
## Alternative constructor (@classmethod)
    
```python
import datetime

class Date:
    def __init__(self, year, month, day):
        self.year = year
        self.month = month
        self.day = day
        print("init")

    @classmethod
    def today_init(cls):
        print("today_init")
        t = datetime.datetime.now()
        return cls(t.year, t.month, t.day)

d = Date.today_init()

print(f"{d.day}/{d.month}/{d.year}")
>>> today_init
>>> init
>>> 15/1/2020
```
## Classmethod vs staticmethod
```python
class Person:  
    def __init__(self, name):  
        self.name = name  
  
    @classmethod  
  def class_met(cls, name):  
        return cls(name)  
  
    @staticmethod  
  def static_met(name):  
        return Person(name)  
  
  
class Man(Person):  
    sex = 'Male'  
  
  
man = Man.class_met('John')  
print(type(man))  
>>> <class '__main__.Man'>
  
man2 = Man.static_met('John')  
print(type(man2))
>>><class '__main__.Person'>
```

## Factory method (@classmethod)
    
**TODO**
```python
class Person:
    def __init__(self, name):
        self.name = name
        
    @classmethod
    def class_met(cls, name):
        return cls(name)

    @staticmethod
    def static_met(name):
        return Person(name)

class Man(Person):
    sex = 'Male'

man = Man.class_met('John')

print(type(man))
>>> <class '__main__.Man'>

man2 = Man.static_met('John')

print(type(man2))
>>> <class '__main__.Person'>
```
  
## Inheritance of @staticmethod and @classmethod
```python
class Foo():
    message = "I'm Foo class"
    
    @classmethod
    def class_method(cls, foo):
        cls.foo = foo
        print(cls.message)

    @staticmethod
    def static_method(foo):
        Foo.foo = foo
        print(Foo.message)

class Bar(Foo):
    message = "I'm Bar class"

  
Foo.class_method(None)
>>> I'm Foo class

Foo.static_method(None)
>>> I'm Foo class

Bar.class_method(None)
>>> I'm Bar class

Bar.static_method(None)
>>>I'm Foo class
```

## Property
 Property is 
 ```python
#start class
class Celsius:
    def __init__(self, temperature = 0):
        self.temperature = temperature

    def to_fahrenheit(self):
        return (self.temperature * 1.8) + 32

 ```
  
##  `_` and `__` prefix 
_ is **private** property, ignored in from module import *

__ is **protected** property, avoid method to be overridden by a subclass.

```python
class MyClass():
    def __init__(self):
        self.__superprivate = "Hello"
        self._semiprivate = "world!"

mc = MyClass()

print(mc.__superprivate)
>>> Error

print(mc._semiprivate)
>>> world!
```
  
```python
class A():
    def __method(self):
        print("I'm a method in A")

    def method(self):
        self.__method()

class B(A):
    def __method(self):
        print("I'm a method in B")

a = A()

a.method()
>>> I'm a method in A

b = B()

b.method()
>>> I'm a method in A
```
  
## Save memory on class instance
What happens here is that when we define `__slots__` attribute, Python uses small fixed-size array for the attributes instead of dictionary, which greatly reduces memory needed for each instance. There are also some downsides to using `__slots__` - we can't declare any new attributes and we are restricted to using ones on `__slots__`. Also classes with `__slots__` can't use multiple inheritance.
```python
class Person:
 __slots__ = ["first_name", "last_name", "phone"]
 def __init__(self, first_name, last_name, phone):
  self.first_name = first_name
  self.last_name = last_name
  self.phone = phone
```
<!--stackedit_data:
eyJwcm9wZXJ0aWVzIjoidGFnczogJ2NsYXNzLCBzdGF0aWNtZX
Rob2QsIGNsYXNzbWV0aG9kLCBjb25zdHJ1Y3RvcidcbiIsImhp
c3RvcnkiOlsyMDY2ODA1ODY0LDE3NDE2NzQzNTUsMjMwMzM0OD
A5LC0xMjQ5OTc1MDM2LC0xNjYyMTE3MTgwLC0xNDU4Nzc2ODc2
LC02Mzg0NjA4ODMsLTQyODcxNTc0MiwzNjY4ODM1MTBdfQ==
-->