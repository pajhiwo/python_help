
# Object Oriented Programming

* **TODO**: check or/and combine with `Inheritance_Composition`

## Encapsulation
Hide internal representation or state of an object, so it is not visible by other external objects - bundling of data with the methods that operate on that data, or the restricting of direct access to some of an object's components

By keeping attributes private (**single underscore “_” prefix**) and only allowing access to them via _getter_ and _setter_ methods, we hide specific information and restrict access to the internal state

## Polymorphism
Polymorphism allows us to define methods in the child class with the same name as defined in their parent class -> Method Overriding


## Abstraction

[Link](https://medium.com/@mrfksiv/python-design-patterns-01-introduction-54e681aaf2d0)

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
eyJoaXN0b3J5IjpbMzU5MzEzMDI5LDIwNDM4MDM3NDIsLTE5ND
I2NTA3NzgsMTM4OTg5MDY4NCwtMzEzMzY5NzA3LDYwNDc5NzEw
NF19
-->