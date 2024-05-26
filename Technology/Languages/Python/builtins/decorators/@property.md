The `@property` decorator in Python is a built-in decorator that allows you to define a method as a "getter" for a class attribute. It provides a convenient way to access and compute values dynamically without directly accessing the attribute itself.

Mechanics of `@property` decorator works:
1. Define a method within a class and decorate it with `@property` above the method definition.
2. This method represents the getter for a specific attribute.
3. When you access the attribute using dot notation on an instance of the class, the decorated method will be automatically called and its return value will be returned instead of accessing the attribute directly.
```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self):
        return self._radius

    @property
    def area(self):
        return 3.14 * self._radius ** 2
```

The `Circle` class has a private attribute `_radius`, which represents the radius of the circle. The `@property` decorator is used to define two methods: `radius` and `area`.

The `radius` method is decorated with `@property`, making it a getter method for the `_radius` attribute. When accessing the `radius` attribute using dot notation on a `Circle` instance, like `circle.radius`, the `radius` method is automatically called and its return value is returned:
```python
my_circle = Circle(5)
print(my_circle.radius)  # Accessing radius attribute using dot notation
# Output: 5
print(my_circle.area)  # Accessing area attribute using dot notation
# Output: 78.5
```