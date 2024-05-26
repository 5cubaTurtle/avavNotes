[askpython](https://www.askpython.com/python/examples/nan-in-numpy-and-pandas)
NaN is short for **Not a number**. It is used to represent entries that are undefined. It is also used for representing missing values in a dataset. NaN is a special floating-point value which cannot be converted to any other type than float.

`np.nan`
```python
import numpy as np
arr = np.array([1, np.nan, 3, 4, 5, 6, np.nan])

arr
>>>  [ 1. nan  3.  4.  5.  6. nan]
```

Calling `arr.sum()` or `arr.max()` for instance will return `nan`. To ignore the `nan` values use `np.nansum(arr)` or `np.nanmax(arr)` instead.
Checking for `nan`: `np.isnan(arr)` >>> *array([False,  True, False, False, False, False,  True])*

### properties
```python
a, b = np.nan, np.nan
a == b # False
a is b # True
```
