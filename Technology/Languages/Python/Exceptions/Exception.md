#python #exception

[quick begginers guide](https://www.pythontutorial.net/python-oop/python-exceptions/)
[realpython intro](https://realpython.com/python-exceptions/)
[google-guide](https://youtu.be/woIkysZytSs?t=781)
![[exception-inheritance.png]]
print the class and message:
```python
colors = ['red', 'green', 'blue']

try:
    print(colors[3])
except Exception as e:
    print(e.__class__, '-', e)
```

to catch several exceptions:
```python
def division(a, b):
    try:
        return {
            'success': True,
            'message': 'OK',
            'result': a / b
        }
    except (TypeError, ZeroDivisionError, Exception) as e:
        return {
            'success': False,
            'message': str(e),
            'result': None
        }

print(division(10, 0))
```

If file not found, raise *FileNotFoundError*:
```python
from pathlib import Path

file_path = Path("example.txt")

if not file_path.exists():
    raise FileNotFoundError(f"The file {file_path} does not exist.")

# or:
import os

filename = 'example.txt'

if not os.path.isfile(filename):
    raise FileNotFoundError(f"The file {filename} does not exist")
```
Note that the `FileNotFoundError` exception is only available in Python 3.x. In Python 2.x, you can use the `IOError` exception instead.

#### finally
the `finally` keyword is used in a `try...except...finally` block to define a section of code that will be executed regardless of whether an exception is raised or not. The `finally` block is often used to ensure that certain resources are properly cleaned up, even if an exception is raised in the `try` block.

Here's an example of how to use a `finally` block:
```python
try:
	# Some code that may raise an exception
	print("Hello, world!")
except:
	# Exception handling code
	print("An exception occurred!")
finally:
	# Clean-up code that will be executed regardless of whether an exception is raised or not
	print("This will always be printed.")
```
This can be useful for closing files, releasing resources, or performing other cleanup tasks that should be done regardless of the outcome of the `try` block.

### Exception types
- `ValueError` is a built-in exception class in Python that represents an error when a function receives an argument of the correct type but an inappropriate value.
-  `StopIteration` exception is raised to signal the end of an iterator. It is a built-in exception that is typically used in conjunction with the iterator protocol to indicate that there are no more items to be retrieved from an iterator. In Python (3.7 and above), `StopIteration` is automatically suppressed and doesn't raise an error when used in a generator. Instead, the generator is considered exhausted, and the iteration simply stops.
- `IndexError` When an out of bounds index is used.

### re-raise exception
```python
except IOError:
	if ignore_existing:
		pass
	else:
		raise
```
Simple passing raise will re-raise the currently caught exception.
