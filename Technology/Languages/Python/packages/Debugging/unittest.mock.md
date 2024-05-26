#python 
mock is a library for testing in Python. It allows you to replace parts of your system under test with mock objects and make assertions about how they have been used.

[Real Python guide](https://realpython.com/python-mock-library/)
#### [The Mock Object](https://realpython.com/python-mock-library/#the-mock-object)
create Mock:
```python
>>> from unittest.mock import Mock
>>> mock = Mock()
>>> mock
<Mock id='4561344720'>
```
use the Mock:
```python
# Pass mock as an argument to do_something()
do_something(mock)

# Patch the json library
json = mock
```
#### [Lazy Attributes and Methods](https://realpython.com/python-mock-library/#lazy-attributes-and-methods)
Mock creates attributes when you access them:
```python
>>> mock.some_attribute
<Mock name='mock.some_attribute' id='4394778696'>
>>> mock.do_something()
<Mock name='mock.do_something()' id='4394778920'>
```
Mock's functions require no arguments and returns also a Mock:
```python
>>> json = Mock()
>>> json.loads('{"k": "v"}').get('k')
<Mock name='mock.loads().get()' id='4379599424'>
```
#### [Assertions and Inspections](https://realpython.com/python-mock-library/#assertions-and-inspection)
assert that your program used an object as you expected:
```python
>>> from unittest.mock import Mock

>>> # Create a mock object
... json = Mock()

>>> json.loads('{"key": "value"}')
<Mock name='mock.loads()' id='4550144184'>

>>> # You know that you called loads() so you can
>>> # make assertions to test that expectation
... json.loads.assert_called()
>>> json.loads.assert_called_once()
>>> json.loads.assert_called_with('{"key": "value"}')
>>> json.loads.assert_called_once_with('{"key": "value"}')

>>> json.loads('{"key": "value"}')
<Mock name='mock.loads()' id='4550144184'>

>>> # If an assertion fails, the mock will raise an AssertionError
... json.loads.assert_called_once()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/Cellar/python/3.6.5/Frameworks/Python.framework/Versions/3.6/lib/python3.6/unittest/mock.py", line 795, in assert_called_once
    raise AssertionError(msg)
AssertionError: Expected 'loads' to have been called once. Called 2 times.

>>> json.loads.assert_called_once_with('{"key": "value"}')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/Cellar/python/3.6.5/Frameworks/Python.framework/Versions/3.6/lib/python3.6/unittest/mock.py", line 824, in assert_called_once_with
    raise AssertionError(msg)
AssertionError: Expected 'loads' to be called once. Called 2 times.

>>> json.loads.assert_not_called()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/Cellar/python/3.6.5/Frameworks/Python.framework/Versions/3.6/lib/python3.6/unittest/mock.py", line 777, in assert_not_called
    raise AssertionError(msg)
AssertionError: Expected 'loads' to not have been called. Called 2 times.
```
To pass these assertions, you must call the mocked method with the same arguments that you pass to the actual method:
```python
>>> json = Mock()
>>> json.loads(s='{"key": "value"}')
>>> json.loads.assert_called_with('{"key": "value"}')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/Cellar/python/3.6.5/Frameworks/Python.framework/Versions/3.6/lib/python3.6/unittest/mock.py", line 814, in assert_called_with
    raise AssertionError(_error_message()) from cause
AssertionError: Expected call: loads('{"key": "value"}')
Actual call: loads(s='{"key": "value"}')
>>> json.loads.assert_called_with(s='{"key": "value"}')
```
View special attributes to understand how your application used an object:
```python
>>> from unittest.mock import Mock

>>> # Create a mock object
... json = Mock()
>>> json.loads('{"key": "value"}')
<Mock name='mock.loads()' id='4391026640'>

>>> # Number of times you called loads():
... json.loads.call_count
1
>>> # The last loads() call:
... json.loads.call_args
call('{"key": "value"}')
>>> # List of loads() calls:
... json.loads.call_args_list
[call('{"key": "value"}')]
>>> # List of calls to json's methods (recursively):
... json.method_calls
[call.loads('{"key": "value"}')]
```

#### [Managing a Mock’s Return](https://realpython.com/python-mock-library/#managing-a-mocks-return-value)

importing Mock: `unittest.mock import Mock`

making sure a function was called
```python
mockObj = Mock()
mockObj.some_func()
mockObj.some_func.assert_called() # will not throw since some_func() has been previously called 
```
Will throw an AssertionError exception if the *some_func* was not called before the assert check.

Test if a function was called 3 times:
```python 
assert mockObj.some_func.call_count == 4
```

set the return value of a Mock to *"return"*:
```python
mockObj.some_func.return_value = "return"
mockObj.some_func()
"return"
```

call your function when Mock object is called:
```python
mockObj = Mock()
mockObj.side_effect = lambda x: x*3
mockObj(4)  # passing parameters to mock(param) will pass it to the side_effect
```

configuring the Mock:
```python
>>> mock = Mock(side_effect=Exception)
>>> mock()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/Cellar/python/3.6.5/Frameworks/Python.framework/Versions/3.6/lib/python3.6/unittest/mock.py", line 939, in __call__
    return _mock_self._mock_call(*args, **kwargs)
  File "/usr/local/Cellar/python/3.6.5/Frameworks/Python.framework/Versions/3.6/lib/python3.6/unittest/mock.py", line 995, in _mock_call
    raise effect
Exception

>>> mock = Mock(name='Real Python Mock')
>>> mock
<Mock name='Real Python Mock' id='4434041432'>

>>> mock = Mock(return_value=True)
>>> mock()
True
```


### chatGPT
The `unittest.mock` module is a powerful tool for testing Python code that uses external dependencies, such as libraries, databases, or web services. It allows you to replace these external dependencies with "mock" objects, which simulate the behavior of the real dependencies but are easier to control and observe during testing.

Here's an example of how to use `unittest.mock` to replace an external dependency with a mock object:

Suppose you have a function called `get_data` that reads data from a file and returns it as a string:
```python
# mymodule.py
def get_data(filename):
    with open(filename, 'r') as f:
        data = f.read()
    return data
```
To test this function using `unittest.mock`, you can create a mock object that simulates the behavior of `open`, and use it to replace the real `open` function during testing. Here's how to do it:
```python
import unittest
from unittest.mock import mock_open, patch
import mymodule

class TestGetData(unittest.TestCase):
    def test_get_data(self):
        # Define the data to be read from the file
        data = "Hello, world!"

        # Create a mock object that simulates the behavior of open
        m = mock_open(read_data=data)

        # Replace the real open function with the mock object
        with patch('builtins.open', m):
            # Call the function to be tested
            result = mymodule.get_data('test.txt')

        # Check that the mock open function was called with the correct filename
        m.assert_called_once_with('test.txt', 'r')

        # Check that the function returned the correct data
        self.assertEqual(result, data)
```

In this code, the `mock_open` function is used to create a mock object that simulates the behavior of `open`. The `read_data` parameter is used to define the data that the mock object should return when `read()` is called.

The `patch` function is used to replace the real `open` function with the mock object. The first parameter to `patch` is a string that specifies the name of the object to be replaced (in this case, `builtins.open`), and the second parameter is the mock object to be used instead.

Inside the `with` block, the `get_data` function is called with the filename `test.txt`. The `assert_called_once_with` method is used to check that the mock `open` function was called with the correct parameters.

Finally, the `self.assertEqual` method is used to check that the function returned the correct data.