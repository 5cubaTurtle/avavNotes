### namedtuple
Using the `namedtuple()` factory function:
```python
from collections import namedtuple

# Create a named tuple class
Person = namedtuple('Person', ['name', 'age', 'city'])

# Create an instance of the named tuple
person1 = Person(name='John', age=30, city='New York')

# Access fields of the named tuple
print(person1.name)  # Output: John
print(person1.age)   # Output: 30
print(person1.city)  # Output: New York
```
 The first argument to `namedtuple()` is the name of the named tuple class, and the second argument is a list of field names as strings.

`namedtuple` provides a convenient way to create lightweight immutable data structures that are similar to tuples but allow accessing fields by name. The field values can be accessed using dot notation.

Note that named tuples are immutable, meaning that their values cannot be changed once they are created. If you need a mutable data structure, you can use the `namedtuple` as a blueprint and create new instances with updated field values:
```python
# Create an instance of the named tuple
person1 = Person(name='John', age=30, city='New York')
print(person1)  # Output: Person(name='John', age=30, city='New York')

# Create a new named tuple with updated values
person2 = person1._replace(age=31, city='San Francisco')
print(person2)  # Output: Person(name='John', age=31, city='San Francisco')
```
The `_replace()` method returns a new named tuple with specified fields replaced by the given values.