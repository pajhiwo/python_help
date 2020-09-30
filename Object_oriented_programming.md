
# Object Oriented Programming
[Link](https://medium.com/@mrfksiv/python-design-patterns-01-introduction-54e681aaf2d0)
* **TODO**: check or/and combine with `Inheritance_Composition`

## Encapsulation
Hide internal representation or state of a structured data object inside a class, so it is not visible by other external objects.
Publicly accessible methods are generally provided in the class (so-called "getters" and "setters") to access the values.

## Polymorphism
**Override** parent class method with child class method with the same name - Static polymorphism
**Overload** method by creating the same name method but with differen parameters - Dynamic polymorphism - not in python


## Abstraction
Handle complexity by hiding unnecessary details from the user - public interface.


## Inheritance
**IS** relationship = Derived class is (inherits from) a Base class.

Derived  class (subclasse, or subtype), derive, inherit, or extends Base  class (super classes) - Derived is a specialized version of Base class.

  
## Composition
**HAS** relationship - Class1 has Class2 objects.

Composite contains an object of another class known as component - composite class has a component of another class.

Class attributes (ex. In init) are considered composition as class HAS those attributes.
```python
class Address:
    def __init__(self, street, city, state, zipcode, street2=''):
        self.street = street
        self.street2 = street2
        self.city = city
        self.state = state
        self.zipcode = zipcode

class Employee:
    def __init__(self, id, name):
        self.id = id
        self.name = name
        self.address = None

manager = Employee(1, 'Mary Poppins')

manager.address = Address(
    '121 Admin Rd',
    'Concord',
    'NH',
    '03301'
)

print(manager.address.street)
>>> 121 Admin Rd
```
or
```python

class Rocket:
    def __init__(self, name, distance):
        self.name = name
        self.distance = distance

    def launch(self):
        return "%s has reached %s" % (self.name, self.distance)


class MarsRoverComp():
    def __init__(self, name, distance, maker):
        self.rocket = Rocket(name, distance) # instantiating the base

        self.maker = maker

    def get_maker(self):
        return "%s Launched by %s" % (self.rocket.name, self.maker)

```
 

## Abstract class, @abstractmethod
Abstract base classes exist to be inherited, but never instantiated. You can use leading underscores in your class name to communicate that objects of that class should not be created.

The abc module in the Python standard library provides functionality to prevent creating objects from abstract base classes.

## Class explosion problem
Too big hierarchical structure of classes

## `__mro__`
The MRO is also used by super() to determine which method or attribute to invoke. MRO shows the order in which Python is going to look for a matching attribute or method.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc5MjI1NjY3LDQxMDE5ODY4OCwtMTcxMj
QzOTkyNywtOTE1NzU4OTQwLDIwNDM4MDM3NDIsLTE5NDI2NTA3
NzgsMTM4OTg5MDY4NCwtMzEzMzY5NzA3LDYwNDc5NzEwNF19
-->