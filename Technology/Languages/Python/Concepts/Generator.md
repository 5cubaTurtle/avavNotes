
[Quick guide](https://treyhunner.com/2018/06/how-to-make-an-iterator-in-python/#Generators:_the_easy_way_to_make_an_iterator), [SO explanation of a generator](https://stackoverflow.com/a/2776865).

Generator is a type of [[Iterator]].
##### generator [class](https://treyhunner.com/2018/06/how-to-make-an-iterator-in-python/#Making_an_iterator:_the_object-oriented_way)
Iterator implemented using a class:
```python
class Count:
    """Iterator that counts upward forever."""

    def __init__(self, start=0):
        self.num = start
  # to allow to using list(Count_object), creating a list
    def __iter__(self):
        return self

  # to allow to using next(Count_object), iterating over the object,
    def __next__(self):
      # also creating an iterator from this object: iter(Count_object)
        num = self.num
        self.num += 1
        return num
```

##### generator function:
```python
def square_all(numbers):
    for n in numbers:
        yield n**2

squares = square_all(favorite_numbers)
```

##### generator expression (generator comprehension)
```python
squares = (n**2 for n in favorite_numbers)
```
