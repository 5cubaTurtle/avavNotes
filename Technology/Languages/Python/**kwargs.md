---
aliases:
  - "*args"
---
[guide](https://realpython.com/python-kwargs-and-args/)

`*args ` used for unpacking a tuple from passed arguments:
```python
def my_sum(*args):
    result = 0
    # Iterating over the Python args tuple
    for x in args:
        result += x
    return result
print(my_sum(1, 2, 3))
```

`**kwargs` used for unpacking a dictionary from passed arguments:
```python
def concatenate(**kwargs):
    result = ""
    # Iterating over the Python kwargs dictionary
    for arg in kwargs.values():
        result += arg
    return result

print(concatenate(a="Real", b="Python", c="Is", d="Great", e="!"))
```