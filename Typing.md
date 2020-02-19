

# Type annotations
Resopurces:
[https://realpython.com/python-type-checking/](https://realpython.com/python-type-checking/)
[https://docs.python.org/3/library/typing.html](https://docs.python.org/3/library/typing.html)
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NTE0MTI1MDAsMTgxNTI5ODA5MywtOD
MyODY5MjIzLDczMDk5ODExNl19
-->