#cpp
Manages the storage of a pointer, providing a limited _garbage-collection_ facility.

Included from *\<memory\>* library. 
Consider the following function signature:
```c++
T* f();
```
There is no way for the caller to know what to do with the pointer after he is done using it. There are several questions arise:
- Is the pointer points to static or heap allocated memory?
- Should it be released with [[Technology/Languages/C++/operators#new|delete]] or [[free]]?

Smart pointers introduced in C++11.
[[unique_ptr]], [[shared_ptr]]
