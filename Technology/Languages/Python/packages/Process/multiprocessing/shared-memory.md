#python #multiprocessing 

[doc](https://docs.python.org/3.8/library/multiprocessing.html#module-multiprocessing.sharedctypes)
##### Sharing data between processes
>**Note:** the following shared memory mechanisms are not *thread-safe*. Use [[Lock]]s to protect them from race-condition.
```python
not_shared_number = 5
```
This cannot be shared between process (it will pass it by value)  

```python
from multiprocessing import Value
shared_number = Value('i', 5) # 'i' is for type int and '5' is the value.
```
Use this to share data between process, it will pass a pointer to shared memory. 

```python
from multiprocessing import Array
shared_array = Array('d', [0.0, 100.0, 200.0])  # 'd' is for type double.
```
The list is slicable (for example `shared_array[:4]`)
 
Passing the value:
```python
p1 = Process(target=foo, args=(lock, shared_number, not_shared_number, shared_array))  
p2 = Process(target=foo, args=(lock, shared_number, not_shared_number, shared_array))
# or as a dictionary:
p2 = Process(target=foo, kwargs=dict(key=value))
```
