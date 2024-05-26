#python #multiprocessing 

[doc](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.Queue)

Queues are thread safe
```python
from multiprocessing import Queue

q = Queue()  # can pass maxsize to it
q.put(("some",data))  # push data to qeueu
some, data = q.get()  # pull data from qeueu
size = q.qsize()  # this is unreliable (approximate size of the qeueu)
```
