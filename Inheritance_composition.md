
# Inheritance and Composition

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
  
## Liskov substitution principle
in a computer program, if S is a subtype of T, then objects of type T may be replaced with objects of type S without altering any of the desired properties of the program. Liskov’s substitution principle is the most important guideline to determine if inheritance is the appropriate design solution.

## Abstract class, @abstractmethod
Abstract base classes exist to be inherited, but never instantiated. You can use leading underscores in your class name to communicate that objects of that class should not be created.

The abc module in the Python standard library provides functionality to prevent creating objects from abstract base classes.

## Class explosion problem
Too big hierarchical structure of classes

## `__mro__`
The MRO is also used by super() to determine which method or attribute to invoke. MRO shows the order in which Python is going to look for a matching attribute or method.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NDc1NzI0NTVdfQ==
-->