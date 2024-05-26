The `global` keyword in Python is used to indicate that a variable is a global variable, which means that it is accessible from anywhere in the program, including from within functions.

When a variable is defined inside a function, it is normally considered a local variable that can only be accessed within that function. However, if you use the `global` keyword before the variable name, you can make that variable accessible from outside the function as well.

```python
count = 0

def increment():
    global count
    count += 1
    print(count)

increment()
increment()
increment()
```
 The `count` variable is defined outside the function, so it is a global variable. Inside the increment function, the global keyword is used to indicate that the count variable is a global variable. This allows the function to access and modify the global count variable.
 