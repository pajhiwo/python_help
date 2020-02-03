# Pytest

## Testing for exception
Here we can see simple context manager that _Pytest_ provides for us. It allows us to specify type of exception that should be raised as well as message of said exception.
```python
import pytest

def test_my_function():
    with pytest.raises(Exception, match='My Message') as e:
        my_function()
        assert e.type is ValueError
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MTg3ODc3NTJdfQ==
-->