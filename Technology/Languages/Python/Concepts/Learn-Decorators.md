#python #decorator #tutorial
This tutorial is based on LinkedIn Python-Beyond-Decorators
1.  Basic decorator,  .\_\_name\_\_ and .\_\_doc\_\_ overite problem,wraps
2. how do we keep the resoult from the function?
```python
from functools import wraps
def make_posh(func):
    '''This is the function decorator'''
    @wraps(func)
    def wrapper():
        '''This is the wrapper function'''
        print("+---------+")
        print("|         |")
        result = func()
        print(result)
        print("|         |")
        print("+=========+")
        return result
    return wrapper

@make_posh
def printname():
    '''Print out your name'''
    return ' Avner '

printname()
```

2.  Using 2 decorators
```python
from functools import wraps

def bold(func):
    '''Bold decorator'''
    @wraps(func)
    def wrapper():
        '''return html bold tags'''
        result = '<b>' + func() + '</b>'
        return result
    return wrapper

def italics(func):
    '''Italics decorator'''
    @wraps(func)
    def wrapper():
        '''return html italics tags'''
        result = '<i>' + func() + '</i>'
        return result
    return wrapper

@bold
@italics
def printfib():
    '''return Fibonacci'''
    return 'Fibonacci'
```
Notice the order of the decorators. The italics applied first and then bold. Try switching the order.

3. What if our function needs to accept arguments? How would the wrapper know which? How many?
```python
from functools import wraps
def decorator(func):    # template decorator
	@wraps(func)
	def wrapper(*args, **kwargs):
		# Do something b4
		result = func(*args, **kwargs)
		# Do something after
		return result
	return wrapper
```

4.  how to time our functions:
```python
from functools import wraps
from time import perf_counter
def timer(func):
	@wraps(func)
	def wrapper(*vargs, **kwargs):
		start = perf_counter()
		result = func(*vargs, **kwargs)
		end = perf_counter()
		print(f"Run duration:{(end-start):.8f}s")
		return result
	return wrapper
```
try timing this Fiboanacci generator:
```python
@timer
def fib(n):
	''' Return the nth value from the Fiboanacci sequence '''
	if n< 2:
	    return n
	else:
		return fib(n-1) + fib(n-2) 
```
5. More verbose timer:
```python
def timer(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = perf_counter()
        result = func(*args, **kwargs)
        end = perf_counter()
        duration = end - start
        arg = str(*args)
        print(f'{func.__name__}({arg}) = {result} -> {duration:.8f}s')
        return result
    return wrapper
```
- [unpacking with the Assterisk operator](https://realpython.com/python-kwargs-and-args/#unpacking-with-the-asterisk-operators)
The biggest benefit of decorators is the separation  of responsabilities. In our function, only code related to the logic of function is visible.

6. Passing parameters to the **decorator**:
```python
from functools import wraps

def munch(start, end):
    def inner_munch(func):
        @wraps(func)
        def wrapper(*vargs, **kwargs):
            food = func()
            tail = (len(food)-start) * 'x' if len(food)<end else 'x'*(end-start)+food[end:]
            result = food[:start] + tail
            return result
        return wrapper
    return inner_munch


@munch(0, 18)
def fib():
    return 'Fibonacci'

```

7. Decorator class:
```python
from functools import update_wrapper
class Count:
    def __init__(self, func):
        update_wrapper(self, func)    # to preserve the __doc__ and __name__ values
        self.func = func
        self.cnt = 0

    def __call__(self, *args, **kwargs):
        self.cnt += 1
        print(f"{self.cnt}")
        result = self.func(*args, **kwargs)
        return result

@Count
def fib(n):
    ''' return the Fibonacci sequence '''
    if n < 2:
        return n
    else:
        return fib(n-1) + fib(n-2)

fib(4)
```

8. Expedite a function using @functools.lru_cache:
```python
from functools import lru_cache
@lru_cache(maxsize=None)
@timer
def fib(n):
	''' Return the nth value from the Fiboanacci sequence '''
	if n< 2:
	    return n
	else:
		return fib(n-1) + fib(n-2)
```

9. host a web server :
	1. set a up a virtual env
	2. install flask:   `pip install flask`
	3. create function to handle server requests:
```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def print_fib():
    return '<h1>Fibonacci</h1>'

@app.route('/fib')
def list_fib():
    return '<b>1, 1, 2, 3, 5, 8, 13, 21 ...</b>'
```
4. read how to use flask:   `flask --help`
5. set env variable:    `export FLASK_APP=flask_fib`
7. start flask server:   `run flask`
8. go to the output link to test the server (http://127.0.0.1:5000) or (http://localhost:5000)
9. read the [Flask class code](https://github.com/pallets/flask/blob/main/src/flask/app.py#L98)
10. read about the *route* function. Try `help(Flask.route)` in *ipython* or [github](https://github.com/pallets/flask/blob/main/src/flask/scaffold.py#L414)
#### Reading material
[RealPython](https://realpython.com/primer-on-python-decorators/)
[[built-in-decorators|built-in decorators]]:
	1. [property](https://docs.python.org/3/library/functions.html#property)
	2. [staticmethod](https://docs.python.org/3/library/functions.html#staticmethod)
	3. [classmethod](https://docs.python.org/3/library/functions.html#classmethod)