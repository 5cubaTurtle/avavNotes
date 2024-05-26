To create an interface class using Python, you can use the `abc` (abstract base classes) module:
```python
from abc import ABC, abstractmethod

class Interface(ABC):
    @abstractmethod
    def method1(self):
        pass
    
    @abstractmethod
    def method2(self, arg):
        pass
```
In this example, we define an abstract base class called Interface. This class has two abstract methods, `method1` and `method2`. Any class that inherits from Interface must implement these two methods.

A class that implements Interface:
```python
class MyClass(Interface):
    def method1(self):
        print("Method 1 called.")
    
    def method2(self, arg):
        print(f"Method 2 called with argument {arg}.")
```
`MyClass` implements both `method1` and `method2`, so it is a valid implementation of Interface.

Use instances of MyClass like any other class:
```python
obj = MyClass()
obj.method1() # Output: "Method 1 called."
obj.method2("Hello") # Output: "Method 2 called with argument Hello."
```
