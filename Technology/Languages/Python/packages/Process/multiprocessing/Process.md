#python #multiprocessing 

[doc](https://docs.python.org/3.8/library/multiprocessing.html#process-and-exceptions)
Start a child process. i.e. run the function *foo* in a child process: `p1 = Process(target=foo)`, then execute `p1.start()`, this must be called at most once per process object.  To pass param to *foo* use: `p1 = Process(target=foo, args=(num,), kwargs=dict(key=value))`

If you want your parent process to wait for the child process: `p1.join()`, this will block the parent until the child finished executing.
The `join(timeout)` function can receive a timeout for the parent to wait. After that time the parent stops being blocked on the `join()` call. The child process continues to run in the background. Notice that the child process could continue running indefinitely even after the parent has died.

[name](https://docs.python.org/3.8/library/multiprocessing.html#multiprocessing.Process.name) a process:`p1 = Process(target=foo, name="Foo")`
