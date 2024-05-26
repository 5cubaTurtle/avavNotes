#python #multiprocessing 

Use a [Lock](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.Lock) to lock a function from being executed by multiple processes:
```python
from multiprocessing import Lock

lock = Lock()
lock.acquire()
# critical section which are protected from race-condition
lock.release()

# or use lock as a context manager:
with lock:
	# critical section
```
