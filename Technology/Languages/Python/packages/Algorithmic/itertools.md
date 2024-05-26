## `itertools`[¶](https://docs.python.org/3/library/itertools.html#module-itertools "itertools: Functions creating iterators for efficient looping.") — [Functions creating iterators for efficient looping](https://docs.python.org/3/library/itertools.html#module-itertools "Permalink to this headline")

### [tee(_iterable_, _n=2_)](https://docs.python.org/3/library/itertools.html#itertools.tee "Permalink to this definition")
Used to create multiple independent iterators from a single [[iterable]]. Useful when there is a need to iterate over the same data multiple times independently.

When you have a single iterator and you want to create multiple independent iterators that can be consumed separately, you can use `tee()`. Each iterator created by `tee()` will produce the same items as the original iterator.

Syntax:
```python
it1, it2, ..., itn = tee(iterable, n=2)
```
- `iterable` is the original [[iterable]] from which the iterators will be created.
- `n` is an optional parameter that specifies the number of independent iterators to create. The default value is 2.

Example:
```python
from itertools import tee

my_list = [1, 2, 3, 4, 5]
it1, it2 = tee(my_list) # Create two independent iterators from the list

for item in it1: # Iterate over the first iterator
    print(item)

for item in it2: # Iterate over the second iterator
    print(item)
```
In this example, `tee()` is used to create two independent iterators (`it1` and `it2`) from the `my_list` iterable. Each iterator can be consumed separately, and they will produce the same items as the original list.

Note that `tee()` creates separate copies of the items in memory, so it can consume additional memory if the iterable is large.

### [zip_longest(_*iterables_, _fillvalue=None_)](https://docs.python.org/3/library/itertools.html#itertools.zip_longest "Permalink to this definition")
Used to combine multiple iterables into a single iterator, where each element of the iterator is a tuple containing elements from the input iterables. The `zip_longest()` function is similar to the built-in `zip()` function, but it handles uneven iterables by filling missing values with a specified fill value.

Syntax:
```python
from itertools import zip_longest
result = zip_longest(*iterables, fillvalue=None)
```
- `iterables` are the input [[iterable]]s that you want to combine. You can pass multiple iterables separated by commas.
- `fillvalue` is an optional parameter that specifies the value used to fill missing values when the iterables have different lengths. The default value is `None`.

The `zip_longest()` function returns an iterator that produces tuples containing elements from each iterable. If the input iterables have different lengths, `zip_longest()` will continue until the longest iterable is exhausted. Missing values from shorter iterables are replaced with the fill value.

Example:
```python
a = [1, 2, 3]
b = ['a', 'b']
c = [10, 20, 30, 40]

result = zip_longest(a, b, c, fillvalue=0)

for item in result:
    print(item)
```
`zip_longest()` combines three iterables (`a`, `b`, `c`) into a single iterator (`result`). The longest iterable is `c`, which has four elements. The missing values from `a` and `b` are replaced with the fill value `0`. The `for` loop iterates over the resulting iterator and prints each tuple containing elements from the input iterables:
```
(1, 'a', 10)
(2, 'b', 20)
(3, 0, 30)
(0, 0, 40)
```

### [groupby(_iterable_, _key=None_)](https://docs.python.org/3/library/itertools.html#itertools.groupby "Permalink to this definition")
`groupby()` is used to group consecutive elements in an iterable based on a specified key function. It returns an iterator that produces tuples containing a key and an iterator of the grouped elements.

```python
from itertools import groupby
result = groupby(iterable, key=None)
```

- `iterable` is the input iterable that you want to group.
- `key` is an optional parameter that specifies a function used to extract the grouping key from each element of the iterable. If `key` is not provided or is `None`, the elements themselves are used as the key.

`groupby()` scans through the iterable and groups consecutive elements that have the same key. The resulting iterator produces tuples where the first element is the key and the second element is an iterator over the grouped elements.
```python
from itertools import groupby
my_list = [1, 1, 2, 2, 2, 3, 4, 4, 5]
result = groupby(my_list)
for key, group in result:
    print(key, list(group))
```
Here, `groupby()` is used to group consecutive elements in the `my_list`. The default behavior is to use the elements themselves as the grouping key. The `for` loop iterates over the resulting iterator, printing each key and the corresponding group of elements as a list:
```
1 [1, 1]
2 [2, 2, 2]
3 [3]
4 [4, 4]
5 [5]
```
The elements with the same value are grouped together, and the iterator produces tuples where the first element is the key (the value of the element) and the second element is an iterator over the grouped elements.

The key function determines how the elements should be grouped. The key function should take an element as input and return a value based on which the elements will be grouped.

The `groupby()` function is useful for tasks that involve grouping and analyzing consecutive elements in an iterable based on certain criteria or patterns.

### cycle
Iterate of a list continuously:
```python
import itertools

my_list = ['a', 'b', 'c', 'd']  # Sample list
cycle_iterator = itertools.cycle(my_list)  # Create an infinite iterator
for item in cycle_iterator:  # Continuously iterate over the lis
    print(item)

```
