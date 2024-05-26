Uses operator overload to provide memory management and safety.

Consider the following function signature:
```c++
T* f();
```
There is no way for the caller to know what to do with the pointer after he is done using it. There are several questions arise:
- Is the pointer points to static or heap allocated memory?
- Should it be released with [[Technology/Languages/C++/operators#new|delete]] or [[free]]?

Smart pointers are introduced in C++11 and refined C++14.
Smart pointers are included from *\<memory\>* library. 
### Unique pointer
- Only one copy of this pointer.
- This pointer cannot be copied (prevented by compiler).
- It's data can be safely destroyed by calling `reset()` on the pointer.
- It's ownership can be transferred by moving it.
- Cannot be passed to a function by value. Only by reference - since it cannot be copied.

Define a unique pointer `ap` to an object `A`:
```c++
class A {...};

std::unique_ptr<A> ap(new A);
```

### Shared pointer
- The user can make copies of it.
- The user can delete those copies.
- Resources will automatically be destroyed when the last copy is deleted.