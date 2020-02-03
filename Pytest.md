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

## Filtering Warnings

With exceptions out of the way, let's look at warnings. Sometimes you get bunch of warning messages in your logs from inside of libraries that you use. You can't fix them and they really just create unnecessary noise, so let's get rid of them:
```python
import warnings
from sqlalchemy.exc import SADeprecationWarning

def test_my_function():
    # SADeprecationWarning is issued by SQLAchemy when deprecated API is used
    warnings.filterwarnings("ignore", category=SADeprecationWarning)
    ...
    assert ...

def test_my_function():
    with warnings.catch_warnings(record=True) as w:
        warnings.simplefilter("ignore")  # ignore annoying warnings
        ...
        assert ...
    # warnings restored
```

Here we show 2 approaches - in first one, we straight up ignore all warnings of specified category by inserting a filter at the front of a filter list. This will cause your program to ignore all warnings of this category until it terminates, that might not always be desirable. With second approach, we use context manager that restores all warnings after exiting its scope. We also specify `record=True`, so that we can inspect list of issued (ignored) warnings if needs be.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzkwMTY3MiwtMTYxODc4Nzc1Ml19
-->