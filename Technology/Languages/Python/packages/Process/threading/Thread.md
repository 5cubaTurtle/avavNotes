[doc](https://docs.python.org/3.12/library/threading.html#threading.Thread)

Constructs a thread:
```python
from threading import Thread
t = Thread(target=print, args=[1], name="name of the thread")
t.run()  # outputs 1

t = Thread(target=print, args=(1,))
t.run()  # outputs 1
```

To run the resultant object in a separate thread us `t.start()`. `t.run()` Will run it in the calling thread.