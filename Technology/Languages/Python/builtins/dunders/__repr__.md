change the behavior in the [[print()]] and in [[ipython]] "out:" representation:
```python
class B:
    def __repr__(self):
        return "Trulalal"

    def foo(self):
        print(self)

b= B()
b.foo()
>>> Trulalal
print(b)
>>> Trulalal
```

[as opposed to \_\_str\_\_](https://saturncloud.io/blog/what-is-the-difference-between-str-and-repr/)
