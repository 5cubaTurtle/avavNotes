[doc](https://python-reference.readthedocs.io/en/latest/docs/dunderdsc/get.html)
The `__get__()` method is a special method in Python that is part of the descriptor protocol. The descriptor protocol allows objects to customize how they are accessed, by defining certain methods that are called when the object is accessed in a particular way.

In particular, the `__get__()` method is called when an attribute of an object is accessed using dot notation. For example, if you have an object `obj` and you access an attribute `obj.attr`, the `__get__()` method of the `attr` object will be called.

The `__get__()` method takes three arguments:

-   `self`: the descriptor object itself
-   `instance`: the instance of the object that is being accessed (or `None` if the attribute is being accessed on the class itself). This argument allows the caller to [[#patch a member function]] of any object without editing the class, even if the method is not static (i.e. uses `self`)
-   `owner`: the class of the instance that is being accessed (this is useful if the descriptor is being shared by multiple classes)

The `__get__()` method should return the value that should be returned when the attribute is accessed. If the attribute is a method, `__get__()` can return a bound method (i.e. a method that has the instance as its first argument).
```python
class MyDescriptor:
    def __get__(self, instance, owner):
        print(f"Getting attribute using MyDescriptor: instance={instance}, owner={owner}")
        return 42
```
use this descriptor in a class, like so:
```python
class MyClass:
    my_attr = MyDescriptor()

obj = MyClass()
print(obj.my_attr)
```
The `__get__()` method of `MyDescriptor` will be called, and it will print:
	"Getting attribute using MyDescriptor: instance=<**main**.MyClass object at 0x...>, owner=<class '**main**.MyClass'>".
It will then return the value `42`, which will be printed by the `print()` statement.

#### patch a member function
The following code changes how a member function of a **specific** instance behaves:
```python
c.capture_raw = c.capture  # the original function is first saved under a different name
def capture_frame(self, encoding=None):  # a patched function defined
    image = self.capture_raw()  # it calles the original
    return Frame(np.frombuffer(image, dtype=np.uint8))  # and makes adjustments to its output
c.capture = capture_frame.__get__(c, c.__class__)  # 
```
This code patches the function `capture()` of the object `c`. The last line uses the ability of `__get__()` to call the function `capture_frame()` with the `self` of the object `c`.
