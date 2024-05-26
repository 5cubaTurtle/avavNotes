Order of inheritance matters. If the same method is defined in multiple parent classes, the method resolution order (MRO) determines which implementation is used. The MRO is determined by the method `__mro__` or by using the `super()` function within methods.

## Initialize one of the parents:
To initialize one of the parent classes, such as `ClassB` in the given example, you can call its `__init__()` method directly:
```python
class ClassA:
    def __init__(self):
        print("Initializing ClassA")

    def method(self):
        print("Method from ClassA")

class ClassB:
    def __init__(self):
        print("Initializing ClassB")

    def method(self):
        print("Method from ClassB")

class MyClass(ClassA, ClassB):
    def __init__(self):
        super().__init__()  # Initialize ClassA since it was inherited 1st
        ClassB.__init__(self)  # Initialize ClassB explicitly

my_obj = MyClass()
my_obj.method() # calls the method of ClassA since it was inherited 1st

# output:
# Initializing ClassA
# Initializing ClassB
# Method from ClassB
```

## Discriminate between parent's methods
To discriminate between method functions of parent classes, you can directly call the specific method of each parent class using the class name:
```python
class MyClass(ClassA, ClassB):
    def method(self):
        ClassA.method(self)  # Call method from ClassA
        ClassB.method(self)  # Call method from ClassB

my_obj = MyClass()
my_obj.method()

# output:
# Method from ClassA
# Method from ClassB
```


