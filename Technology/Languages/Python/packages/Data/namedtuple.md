Useful for creating readable data structures.
[guide](https://dbader.org/blog/writing-clean-python-with-namedtuples)

`from collections import namedtuple`
```python
Car = namedtuple('Car' , 'color mileage')
# or
Car = namedtuple('Car' , ['color', 'mileage'])

mycar = Car('red', 223000.0)
print("I have a", mycar)
# or
print("my car is", mycar.color, "and it drove", mycar.mileage, "miles")
```
