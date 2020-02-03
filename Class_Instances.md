# Class instances (Objects)
Every object has an identity, a type and a value. Object’s identity never changes once it has been created; you may think of it as the object’s address in memory. Objects are never explicitly destroyed; however, when they become unreachable
  
## `Object.__new__(cls, [, ...])`
Creates a new instance of class - object.

Takes the class of which an instance was requested as its first argument.

The remaining arguments are passed to the object constructor.

If `__new__()` is invoked, it returns an (object) instance or subclass of cls, then the new instance’s `__init__()` method will be invoked

[https://docs.python.org/3/reference/datamodel.html?highlight=__new__#object.__new__](https://docs.python.org/3/reference/datamodel.html?highlight=__new__#object.__new__)
  
## `Object.__init__(self, [, ...])`
Customize a new instance of class - object.

Called after the instance has been created (by `__new__()`), but before it is returned to the caller.

The arguments are passed to the class constructor expression

[https://docs.python.org/3/reference/datamodel.html?highlight=__new__#object.__init__](https://docs.python.org/3/reference/datamodel.html?highlight=__new__#object.__init__)
  
## `Object.__del__(self)`
Destroys the instance. It is not a destructor

[https://docs.python.org/3/reference/datamodel.html?highlight=__new__#object.__del__](https://docs.python.org/3/reference/datamodel.html?highlight=__new__#object.__del__)
  
## `__repr__() and __str__()`
Returns string representation of an object

`__repr__` - unambiguous -> usually eval will convert it back to that object

`__str__` - readable

[https://docs.python.org/3/reference/datamodel.html?highlight=__new__#object.__repr__](https://docs.python.org/3/reference/datamodel.html?highlight=__new__#object.__repr__)
  
## Object resurrection
Postpone destruction of the instance by creating a new reference to it in `__del__`
  
## Delete properties on objects
by using the `del` keyword
  
## Copy object
### Shallow copy
`copy.copy()` or `copy.deepcopy()`
  
## Rich comparison
`object.__lt__(self, other), object.__le__(self, other), object.__eq__(self, other), object.__ne__(self, other), object.__gt__(self, other), object.__ge__(self, other)`
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI2MjYwNDA3OF19
-->