Enumerations in Python provide a convenient way to define a fixed set of named values. They help improve code readability and maintainability by explicitly defining a limited set of possible values and preventing invalid assignments.

Create an enumeration using the `enum` module:
```python
from enum import Enum

class Color(Enum):
    RED = 1
    GREEN = 2
    BLUE = 3
```
You can access the enumeration members using dot notation, like `Color.RED`, `Color.GREEN`, or `Color.BLUE`. The members behave like constants and can be used in comparisons and other operations.

Here are a few examples of how to use the `Color` enumeration:
```python
# Accessing enumeration members
print(Color.RED)         # Output: Color.RED
print(Color.GREEN)       # Output: Color.GREEN
print(Color.BLUE)        # Output: Color.BLUE

# Comparing enumeration members
if Color.RED == Color.GREEN:
    print("Colors are equal")
else:
    print("Colors are not equal")  # Output: Colors are not equal

# Iterating over enumeration members
for color in Color:
    print(color)            # Output: Color.RED, Color.GREEN, Color.BLUE
```
To get an Enum's *str* name use `Color.BLUE.name`. This resolves to `'BLUE'`.
To get the *int* value use `Color.BLUE.value`. This resolves to `3`.

### EnumMeta
The `enum.EnumMeta` is a metaclass used by the `enum.Enum` class to define enumerations in Python. It is responsible for creating and configuring the enumeration class based on the definitions provided within it.

The primary purpose of the `enum.EnumMeta` is to handle the following tasks:

1. Validating enumeration member names: It ensures that each member name within the enumeration is unique, preventing duplicate names.
2. Assigning values to enumeration members: If explicit values are not provided for enumeration members, the metaclass automatically assigns unique values based on their order of definition.
3. Creating enumeration attributes: The metaclass creates attributes for each enumeration member, allowing easy access to the members using dot notation.
4. Enforcing enum member uniqueness: It ensures that the enumeration members are unique by comparing them using the `is` operator.
5. Providing iteration support: The metaclass enables iterating over the enumeration members in the order of their definition.

The `enum.EnumMeta` metaclass is an essential part of the `enum` module's functionality. It handles the underlying mechanics of creating and configuring enumeration classes, making it easier for developers to define and use enumerations in their code.