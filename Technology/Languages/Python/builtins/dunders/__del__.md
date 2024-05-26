special method called `__del__` could be used to perform cleanup operations when an object is **garbage collected**
```python
class MyObject:
    def __init__(self):
        # Initialize the object
        pass
    
    def __del__(self):
        # Perform cleanup operations
        print('Object deleted')
```

Note that the `__del__` method is not guaranteed to be called at any specific time, and should not be relied upon for critical cleanup operations. In general, it's better to use [[contex-manager|context managers]], [[Exception|`try/finally`]] blocks, or other mechanisms to ensure that cleanup operations are performed properly.