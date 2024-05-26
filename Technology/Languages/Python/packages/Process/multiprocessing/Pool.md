#python #multiprocessing 

Process [pool](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool). Used for distributing work among several processes.
>Note that the methods of the pool object should only be called by the process which created the pool.

import: `from multiprocessing import Pool`
create a Pool: `pool = Pool()`
operate on an iterable(list) in parallel: `pool.map(foo, iterable)`, this returns a list of results from function *foo* acting(receiving as argument) on each element of *iterable*.
##### map
```python
result = pool.map(cube, numbers)
```
This will execute cube(numbers\[i\]) in parallel by as many processes as the Pool created (usually as many free cores are available)
 
##### apply
```python
print(pool.apply(cube, (numbers[4],)))
```
`apply` takes a function and `*args` and/or `**kwds`. Thus, we pass here a tuple (an iterable which could be expanded by the `*` operator) instead of just the `numbers[4]`

>**Warning**:
>[`multiprocessing.pool`](https://docs.python.org/3.8/library/multiprocessing.html#module-multiprocessing.pool "multiprocessing.pool: Create pools of processes.") objects have internal resources that need to be properly managed (like any other resource) by using the pool as a context manager or by calling [`close()`](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool.close "multiprocessing.pool.Pool.close") and [`terminate()`](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool.terminate "multiprocessing.pool.Pool.terminate") manually. Failure to do this can lead to the process hanging on finalization.

Note that its **not correct** to rely on the garbage collector to destroy the pool as CPython does not assure that the finalizer of the pool will be called (see [`object.__del__()`](https://docs.python.org/3.8/reference/datamodel.html#object.__del__ "object.__del__") for more information).

`close`()[¶](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool.close "Permalink to this definition")
Prevents any more tasks from being submitted to the pool. Once all the tasks have been completed the worker processes will exit.

`terminate`()[¶](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool.terminate "Permalink to this definition")
Stops the worker processes immediately without completing outstanding work. When the pool object is garbage collected [`terminate()`](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool.terminate "multiprocessing.pool.Pool.terminate") will be called immediately.

`join`()[¶](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool.join "Permalink to this definition")
Wait for the worker processes to exit. One must call [`close()`](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool.close "multiprocessing.pool.Pool.close") or [`terminate()`](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool.terminate "multiprocessing.pool.Pool.terminate") before using [`join()`](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool.join "multiprocessing.pool.Pool.join").

>Pool objects support the context management protocol – see [Context Manager Types](https://docs.python.org/3.8/library/stdtypes.html#typecontextmanager). [`__enter__()`](https://docs.python.org/3.8/library/stdtypes.html#contextmanager.__enter__ "contextmanager.__enter__") returns the pool object, and [`__exit__()`](https://docs.python.org/3.8/library/stdtypes.html#contextmanager.__exit__ "contextmanager.__exit__") calls [`terminate()`](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.pool.Pool.terminate "multiprocessing.pool.Pool.terminate").

##### sample code
```python
from multiprocessing import Pool  
  
def cube(number):  
    return number * number * number  
  
if __name__ == "__main__":  
  
    pool = Pool()  
    numbers = range(101)  
    result = pool.map(cube, numbers)    # this will execute cube(numbers[i]) in parallel by as many processes as the Pool created (usually as many free cores are available)
    print(pool.apply(cube, (numbers[4],)))  # apply take a function and *args and/or **kwds. Thus, we pass here a tuple (an iterable which could be expanded by the '*' operator) instead of just the 'numbers[4]'
    pool.close()    # close the Pool it can be joined  
    pool.join()     # join the pool to wait for it to finish  
    print(result)  
  
    # other useful functions of Pool: apply, join, close
```