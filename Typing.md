

# Type annotations

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
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgxNTI5ODA5MywtODMyODY5MjIzLDczMD
k5ODExNl19
-->