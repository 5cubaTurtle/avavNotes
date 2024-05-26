#python #multiprocessing
[python docs](https://docs.python.org/3/library/multiprocessing.html)
[quick video guide](https://youtu.be/IT8RYokUvvQ)
[guidelines](https://docs.python.org/3.8/library/multiprocessing.html#programming-guidelines)

[[Process]] [[shared-memory]] [[Lock]] [[Pipe]] [[Queue]] [[Pool]]
sample code:
```python
from multiprocessing import Process, Lock, Value, Array, Queue  
  
def print_hi(name):  
    print(f'Hi, {name}')  # Press Ctrl+F8 to toggle the breakpoint.  
  
def foo(lock:Lock(), shrd_num, num, array, queue, name="Jejo"):  
    # with lock:  
        for n in range(500):  
            shrd_num.value += 1  
            num += 1  
            if n < len(array):  
                array[n] += 1  
            print_hi(f"{name} {str(n)}, shared val: {str(shrd_num)}, not shared: {num}, array:{array[:]}")  # array[:] is done so we take the values of the object and not the <SynchronizedArray wrapper for <multiprocessing.sharedctypes.c_double_Array at 0x...>  
            if q.empty():  
                q.put((f"{name} pushed {n}", n))  
                print(f"{name} pushed {n}, Q size:{q.qsize()}")  
            else:  
                print(f"{name} got {q.get()} from the Queue({q.qsize()})")  
  
  
if __name__ == '__main__':  
    not_shared_number = 5   # this cannot be shared between process (it will pass it by value)  
    shared_number = Value('i', 5)   # Use this to share data between process, it will pass a pointer to shared memory. 'i' is for type int and '5' is the starting value.  
    shared_array = Array('d', [0.0, 100.0, 200.0])  # 'd' is for type double. The list is slicable (for example shared_array[:4])  
    lock = Lock()  
    q = Queue()  
    p1 = Process(target=foo, args=(lock, shared_number, not_shared_number, shared_array, q))  
    steve = Process(target=foo, args=(lock, shared_number, not_shared_number, shared_array, q, "Steve"))  
    print("starting steve")  
    steve.start()  
    # steve.join()  
    print("starting p1")  
    p1.start()  
    p1.join(2)  # wait for 2 seconds for the process to finish, then continue with the execution.  
    print_hi('PyCharm End')
```

Also see [asyncio](https://docs.python.org/3/library/asyncio.html)
