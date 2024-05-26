```python
class A:  
    def foo(self):  
        print("A foo")  
  
    def bar(self):  # when this called from derived class the 'self' is of the derived class!
        print("A bar")  
        self.foo()  # if called by derived class, the overriden function of the derived class will be called instead of the function of the base class.
  
class B (A):  
    def foo(self):  
        print("B foo")  
  
if __name__ == "__main__":  
    b = B()  
    b.foo()  
    b.bar() # this calls for b's foo

# output:
>>> B foo
>>> A bar
>>> B foo
```
This demonstrates that the `self` reference is dependent on the caller object.
