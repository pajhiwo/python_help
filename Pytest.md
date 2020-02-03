# Pytest

## Testing for exception
```python
import pytest

def test_my_function():
    with pytest.raises(Exception, match='My Message') as e:
        my_function()
        assert e.type is ValueError
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5ODkwMzcyNjBdfQ==
-->