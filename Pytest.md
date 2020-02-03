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

## Testing Standard Output and Standard Error Messages

Next, let's look at following scenario: You have a command line tool that has bunch of functions that print messages to standard output but don't return anything. So, how do we test that?

```python
def test_my_function(capsys):
    my_function()  # function that prints stuff
    captured = capsys.readouterr()  # Capture output
    assert f"Received invalid message ..." in captured.out  # Test stdout
    assert f"Fatal error ..." in captured.err  # Test stderr
```

## Mock
It's possible to patch functions and then check how many times and with what arguments they were called - in form of decorator and context manager
```python
from unittest import mock

def test_my_function():
    with mock.patch('module.some_function') as some_function:  # Used as context manager
        my_function()  # function that calls `some_function`

        some_function.assert_called_once()
        some_function.assert_called_with(2, 'x')

@mock.patch('module.func')  # Used as decorator
def test_my_function(some_function):
    module.func(10)  # Calls patched function
    some_function.assert_called_with(10)  # True
```

We can replace method of `SomeClass` and make it return `None`
```python
from unittest import mock

def test_my_function():
    with mock.patch.object(SomeClass, 'method_of_class', return_value=None) as mock_method:
        instance = SomeClass()
        instance.method_of_class('arg')

        mock_method.assert_called_with('arg')  # True
```

We can avoid being dependent on remote API/resource by replacing `requests.get` by mock and making it return object that we supply with suitable data.
```python
from unittest import mock

def test_my_function():
    r = Mock()
    r.content = b'{"success": true}'
    with mock.patch('requests.get', return_value=r) as get:  # Avoid doing actual GET request
        some_function()  # Function that calls requests.get
        get.assert_called_once()
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTgyODczNzYsMTE1OTA3NzQ3NiwtMT
YxODc4Nzc1Ml19
-->