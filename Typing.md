

# Type annotations
Resopurces:
[https://realpython.com/python-type-checking/](https://realpython.com/python-type-checking/)
[https://docs.python.org/3/library/typing.html](https://docs.python.org/3/library/typing.html)
[https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html)
[https://mypy.readthedocs.io/en/stable/kinds_of_types.html](https://mypy.readthedocs.io/en/stable/kinds_of_types.html)

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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM0OTc4MDM0LDEyODIzNDI4NDEsLTE4NT
E0MTI1MDAsMTgxNTI5ODA5MywtODMyODY5MjIzLDczMDk5ODEx
Nl19
-->