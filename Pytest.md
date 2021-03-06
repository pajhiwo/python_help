# Pytest
sources:
* https://martinheinz.dev/blog/7

Most functional tests follow the Arrange-Act-Assert model:

1.  **Arrange**, or set up, the conditions for the test
2.  **Act**  by calling some function or method
3.  **Assert**  that some end condition is true

## CMD arguments
**-s** :   show print from code
**-p no:warning** : do not show warnings
**-m** : select mark

## Execution
-   **Name-based filtering**: You can limit  `pytest`  to running only those tests whose fully qualified names match a particular expression. You can do this with the  `-k`  parameter.
-   **Directory scoping**: By default,  `pytest`  will run only those tests that are in or under the current directory.
-   **Test categorization**:  `pytest`  can include or exclude tests from particular categories that you define. You can do this with the  `-m`  parameter.

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
## Mocker
Mocker is pytest wrapper around Mock used as fixture. Can be used in the same way as Mock
```python
def test_something(mocker):
  sut = SUT()
  sut.mocked_method() = mocker.Mock(return_value=[1, 2]) # mocket_method will return 1 on 1st call and 2 on 2nd
  sut.mocked_method = mocker.Mock(side_effect=Exception()) # will raise exception on a mocked_method call
  
  mocked_builtin = mocker.patch("path.to.module.where.builtin.is.used.glob.glob)
  mocked_builtin.return_value = "aaa"  # patch glob.glob in given module
  # or in 1 line
  mocker.patch("path.to.module.where.builtin.is.used.glob.glob).return_value = "aaa"
```

## Conftest
`conftest.py` is a file which resides at base of your test directory tree. In this file you can store all test fixtures and these are then automatically discovered by _Pytest_, so you don't even need to import them. This is also helpful if you need to share data between multiple tests. 
Possible scopes for fixture are: `function`, `class`, `module`, `package` and `session`.

## Parametrizing Fixtures

```python
import pytest, os

@pytest.fixture(scope='function')
def reset_sqlite_db(request):
    path = request.param  # Path to database file
    with open(path, 'w'): pass
    yield None
    os.remove(path)

@pytest.mark.parametrize('reset_sqlite_db', ['/tmp/test_db.sql'], indirect=True)
def test_send_message(reset_sqlite_db):
    ...  # Perform tests that access prepared SQLite database
```
This fixture receives path to the database as parameter. This path is passed to the fixture using the `request` object, which attribute `param` is an iterable of all arguments passed to the fixture, in this case just one - the path.
We use `@pytest.mark.parametrize` with 3 arguments - first of them is name of the fixture, second is a list of argument values for the fixture which will become the `request.param` and finally keyword argument `indirect=True`, which causes the argument values to appear in `request.param`.

## Skipping Tests
Example of how you can skip a valid test based on some condition
```python
import pytest, os

@pytest.mark.skipif(os.system("service postgresql status") > 0,
                    reason="PostgreSQL service is not running")
def test_connect_to_database():
    ... # Run function that tries to connect to PostgreSQL database
```


## Checking for Exceptions
Check that the exception is raised by the SUT
```python
def test_something():
  with pytest.raises(ExceptionType, match="optional Exception re text to match")
    call_SUT()
```

## Monkeypatching
https://docs.pytest.org/en/latest/monkeypatch.html
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMxOTkzOTE3MiwxNTg5MzI0Njc4LDk1NT
c4MTEzNSw2NDY4MzQ3MjYsLTE3MjM2MjYwNDksMTA0NjU0OTgy
MCwxMDA0ODY3MDM2LDcwNzQxMTIwMiwxMTg5NTMwNjAyLDExNT
kwNzc0NzYsLTE2MTg3ODc3NTJdfQ==
-->