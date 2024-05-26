[doc](https://pypi.org/project/natsort/)
Simple yet flexible natural sorting in Python.

## Quick Description
When you try to sort a list of strings that contain numbers, the normal python sort algorithm sorts lexicographically, so you might not get the results that you expect:
```python
>>> a = ['2 ft 7 in', '1 ft 5 in', '10 ft 2 in', '2 ft 11 in', '7 ft 6 in']
>>> sorted(a)
['1 ft 5 in', '10 ft 2 in', '2 ft 11 in', '2 ft 7 in', '7 ft 6 in']
```
Notice that it has the order (‘1’, ‘10’, ‘2’) - this is because the list is being sorted in lexicographical order, which sorts numbers like you would letters (i.e. ‘b’, ‘ba’, ‘c’).

[natsort](https://natsort.readthedocs.io/en/stable/index.html) provides a function [natsorted()](https://natsort.readthedocs.io/en/stable/api.html#natsort.natsorted) that helps sort lists “naturally” (“naturally” is rather ill-defined, but in general it means sorting based on meaning and not computer code point). Using [natsorted()](https://natsort.readthedocs.io/en/stable/api.html#natsort.natsorted) is simple:
```python
>>> from natsort import natsorted
>>> a = ['2 ft 7 in', '1 ft 5 in', '10 ft 2 in', '2 ft 11 in', '7 ft 6 in']
>>> natsorted(a)
['1 ft 5 in', '2 ft 7 in', '2 ft 11 in', '7 ft 6 in', '10 ft 2 in']
```
[natsorted()](https://natsort.readthedocs.io/en/stable/api.html#natsort.natsorted) identifies numbers anywhere in a string and sorts them naturally.

This is great for sorting filenames
