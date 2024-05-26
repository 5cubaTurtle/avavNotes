#python #multiprocessing 

[Pipe vs Queue](https://superfastpython.com/multiprocessing-pipe-in-python/#Pipe_vs_Queue)
The [`Pipe()`](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.Pipe "multiprocessing.Pipe") function returns a pair of connection objects connected by a pipe which by default is duplex (two-way). For example:
```python
from multiprocessing import Process, Pipe

def f(conn):
    conn.send([42, None, 'hello'])
    conn.close()

if __name__ == '__main__':
    parent_conn, child_conn = Pipe()
    p = Process(target=f, args=(child_conn,))
    p.start()
    print(parent_conn.recv())   # prints "[42, None, 'hello']"
    p.join()
```
The two connection objects returned by [`Pipe()`](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.Pipe "multiprocessing.Pipe") represent the two ends of the pipe. Each connection object has `send()` and `recv()` methods (among others). Note that data in a pipe may become corrupted if two processes (or threads) try to read from or write to the _same_ end of the pipe at the same time. Of course there is **no risk of corruption** from processes using different ends of the pipe at the same time.

By default a Pipe is create as duplex (sending/receiving both ways). If we set the *duplex* param in the constractor to false, we will get a one-way Pipe: 
`receiving_connection, sending_connection = Pipe(false)` or `Pipe(duplex=False)`

 >If the Pipe is full, the sender blocks. i.e. if the sender sends and no-one receives, the pipe will fill up and the next call of `send()` will block. [Stack overflow answer](https://stackoverflow.com/a/12273336/5273667).
