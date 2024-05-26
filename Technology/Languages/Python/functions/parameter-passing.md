#python 
[SO question](https://stackoverflow.com/questions/1132941/least-astonishment-and-the-mutable-default-argument?rq=1)
[mutable default param](https://web.archive.org/web/20200221224620id_/http://effbot.org/zone/default-values.htm)
```python
def foo(a=[]):
    a.append(5)
    return a
```

Python novices would expect this function called with no parameter to always return a list with only one element: `[5]`. The result is instead very different, and very astonishing (for a novice):

```python
>>> foo()
[5]
>>> foo()
[5, 5]
>>> foo()
[5, 5, 5]
>>> foo()
[5, 5, 5, 5]
>>> foo()
```