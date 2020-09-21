

# Type annotations
Resopurces:
[https://realpython.com/python-type-checking/](https://realpython.com/python-type-checking/)
[https://docs.python.org/3/library/typing.html](https://docs.python.org/3/library/typing.html)
[https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html)
[https://mypy.readthedocs.io/en/stable/kinds_of_types.html](https://mypy.readthedocs.io/en/stable/kinds_of_types.html)
[Link](https://www.python.org/dev/peps/pep-0526/#id4)

## Basic type annotation
```python
nothing: str
pi: float = 3.142

def circumference(radius: float) -> float:
    return 2 * pi * radius
```

## Typing module
Specify the types of elements of composite types.
```python
from typing import Dict, List, Tuple

names: List[str] = ["Guido", "Jukka", "Ivan"]
version: Tuple[int, int, int] = (3, 7, 1)
options: Dict[str, bool] = {"centered": False, "capitalize": True}
other: List[Tuple[str,str]] = [("str1", "str2"), ("str3", "str4")]
```
In many cases your functions will expect some kind of sequence, and not really care whether it is a list or a tuple. In these cases you should use `typing.Sequence`

## Type aliases
```python
Card = Tuple[str, str]
Deck = List[Card]
```

## Any type
```python
from typing import Any, Sequence

def choose(items: Sequence[Any]) -> Any:
    return random.choice(items)

or

x: Any = mystery_function()
```
`items` is a sequence that can contain items of any type


## Union type
Use Union when something could be one of a few types
```python
x: List[Union[int, str]] = [3, 5, "test", "fun"]
```

## Optional
`Optional` type simply says that a variable either has the type specified or is `None`.
```python

def player_order(start=None):
->
def player_order(start: Optional[str] = None):
```

## Type variable
A type variable is a special variable that can take on any type, depending on the situation. 
A type variable must be defined using `TypeVar` from the `typing` module. 
When used, a type variable ranges over all possible types and takes the most specific type possible.
TypeVar()' must be a string equal to the variable name to which it is assigned.
```python

import random
from typing import Sequence, TypeVar

Choosable = TypeVar("Chooseable")

def choose(items: Sequence[Choosable]) -> Choosable:
    return random.choice(items)

names = ["Guido", "Jukka", "Ivan"]
reveal_type(names)

name = choose(names)
reveal_type(name)
```
In the example, `name` is now a `str`





<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNDI2MTE4MzgsMTg2MjkwODE3OSwtMj
AyMzIwNzU3MywtMzQ5NzgwMzQsMTI4MjM0Mjg0MSwtMTg1MTQx
MjUwMCwxODE1Mjk4MDkzLC04MzI4NjkyMjMsNzMwOTk4MTE2XX
0=
-->