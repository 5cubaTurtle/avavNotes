[SO](https://stackoverflow.com/a/279586)
```python
def foo():
    foo.counter += 1
    print "Counter is %d" % foo.counter
foo.counter = 0
```

If you want the counter initialization code at the top instead of the bottom, you can create a decorator:
```python
def static_vars(**kwargs):
    def decorate(func):
        for k in kwargs:
            setattr(func, k, kwargs[k])
        return func
    return decorate
```

Then use the code like this:
```python
@static_vars(counter=0)
def foo():
    foo.counter += 1
    print "Counter is %d" % foo.counter
```