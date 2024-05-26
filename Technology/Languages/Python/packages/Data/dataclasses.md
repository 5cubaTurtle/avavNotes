#python 
[RealPython](https://realpython.com/python-data-classes/)  <-  [bookmark](https://realpython.com/python-data-classes/#adding-methods)

Usage-:
```python
from dataclasses import dataclass, field
from typing import Any, ClassVar

@dataclass
class Position:
    name: str
    lon: float
	move: Any  # type 'Any' is like not defining any type
    lat: float = 0.0  # default value
	timers: ClassVar = {} # makes this a class variable (shared by all instances)
	_start_time: Any = field(default=None, init=False, repr=False)

	def __post_init__(self):
		"""this runs after init"""
		print('post')
```
>Make sure to place the default values last.

The `_start_time` field uses the `field` feature of *dataclasses*. This allows removing of the variable `_start_time` from the `__init__()` and `__repr__()` functions of the class.

`__post_init__()` method for any initialization that you need to do apart from setting the instance attributes.