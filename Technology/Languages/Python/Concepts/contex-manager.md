#python 
[RealPython](https://realpython.com/python-with-statement/)

```python
with EXPRESSION as VARIABLE:
    BLOCK
```
`EXPRESSION` is some Python expression that returns a context manager. The context manager is **optionally** bound to the name `VARIABLE`. `BLOCK` is any regular Python code block. The context manager will guarantee that your program calls some code before `BLOCK` and some other code after `BLOCK` executes. The latter will happen, even if `BLOCK` raises an exception.

The most common use of context managers is probably handling different resources, like files, locks, and database connections. The context manager is then used to free and clean up the resource after you’ve used it.

Example:
```python
with open("timer.py") as fp:
	print("".join(ln for ln in fp if ":" in ln))
```

What does it mean that `fp` is a context manager? Technically, it means that `fp` implements the **context manager protocol**. There are many different [protocols](https://www.python.org/dev/peps/pep-0544/) underlying the Python language. You can think of a protocol as a contract that states what specific methods your code must implement.

The [context manager protocol](https://docs.python.org/3/reference/datamodel.html#with-statement-context-managers) consists of two methods:

1.  Call `__enter__()` when entering the context related to the context manager.
2.  Call `__exit__()` when exiting the context related to the context manager.

In other words, to create a context manager yourself, you need to write a class that implements `.__enter__()` and `.__exit__()`.

example:
```python
# greeter.py
class Greeter:
	def __init__(self, name):
        self.name = name

    def __enter__(self):
        print(f"Hello {self.name}")
        return self

    def __exit__(self, exc_type, exc_value, exc_tb):
        print(f"See you later, {self.name}")
```
In this simplified example, you’re not referencing the context manager. In such cases, you don’t need to give the context manager a name with `as`.

Next, notice how `.__enter__()` returns `self`. The return value of `.__enter__()` is bound by `as`. You usually want to return `self` from `.__enter__()`
`__exit__()` takes three arguments: `exc_type`, `exc_value`, and `exc_tb`. These are used for error handling within the context manager, and they mirror the [return values of `sys.exc_info()`](https://docs.python.org/3/library/sys.html#sys.exc_info).
- If you are not going to handle the exception int your `__exit__()`, then it could be written more succinctly as `__exit__(self, *exc_info):` This will pack the 3 arguments `exc_type, exc_value, exc_tb` into a *tuple*.
