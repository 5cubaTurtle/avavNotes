#python 

usage:
```python
def func(arg: arg_type, optarg: arg_type = default) -> return_type:
    ...
```

several options for a type of a parameter:
```python
def __init__(self, widen: int or None = 50):
	...
```
- variable *widen* intended to be either an `int` or a `None`

Annotations are stored in a special `.__annotations__` attribute on the function:
```python
import math
def circumference(radius: float) -> float:
	return 2 * math.pi * radius

>>> circumference.__annotations__
{'radius': <class 'float'>, 'return': <class 'float'>}
>>> circumference(1.23)
7.728317927830891`
```

#### Variable annotations
```python
>>> pi: float = 3.142
>>> def circumference(radius: float) -> float:
>>>     return 2 * pi * radius

>>> circumference.__annotations__
{'radius': <class 'float'>, 'return': <class 'float'>}

>>> __annotations__
{'pi': <class 'float'>}

>>> circumference(1)
6.284
>>> nothing: str

>>> nothing
Traceback (most recent call last):
  File "<input>", line 1, in <module>
    nothing
NameError: name 'nothing' is not defined
>>> __annotations__
{'pi': <class 'float'>, 'nothing':<class 'str'>}
```


### [Return several types](https://stackoverflow.com/a/33945518/5273667)
#### return two types (a tuple)
```python
from typing import Tuple

def my_function() -> Tuple[int, str]:
    return 42, "hello"
```

#### return one or the other
From the [documentation](https://docs.python.org/3/library/typing.html#typing.Union)
> class `typing.Union`
> Union type; _**Union[X, Y] means either X or Y.**_

Hence the proper way to represent more than one return data type is
```python
from typing import Union
def foo(client_id: str) -> Union[list,bool]
```
