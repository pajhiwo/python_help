

# Type annotations
Resopurces:
[Link](https://realpython.com/python-type-checking/)
## Basic type annotation
```python
nothing: str
pi: float = 3.142

def circumference(radius: float) -> float:
    return 2 * pi * radius
```

## typing module
Specify the types of elements of composite types.
```python
from typing import Dict, List, Tuple

names: List[str] = ["Guido", "Jukka", "Ivan"]
version: Tuple[int, int, int] = (3, 7, 1)
options: Dict[str, bool] = {"centered": False, "capitalize": True}
other: List[Tuple[str,str]] = [("str1", "str2"), ("str3", "str4")]
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzODM5MzcwNDQsMTgxNTI5ODA5MywtOD
MyODY5MjIzLDczMDk5ODExNl19
-->