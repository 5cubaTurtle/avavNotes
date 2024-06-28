#cpp
[doc](https://devdocs.io/cpp/memory/unique_ptr)

- Only one copy of this pointer.
- This pointer cannot be copied (prevented by compiler).
- It's data can be safely destroyed by calling `reset()` on the pointer.
- It's ownership can be transferred by moving it.
- Cannot be passed to a function by value. Only by reference - since it cannot be copied.

Defining a unique pointer to an object `A`:
```c++
std::unique_ptr<T> ptr(new T);
std::unique_ptr ptr = std::make_unique<T>();  //untill c++20
```
[SO question](https://stackoverflow.com/q/53870522/24231920) and [C++ FAQ](https://isocpp.org/blog/2019/06/quick-q-differences-between-stdmake-unique-and-stdunique-ptr-with-new) explain the purpose of `make_unique`.

Only the `unique_ptr`'s are destroyed automatically when out of scope:
```c++
int main() {
    std::unique_ptr<A> uptr0;  // empty pointer. i.e does not point to anything
    cout << "===Begin code block===" << endl;
    {
        A* leaky_ptr = new A;
        A* a = new A;
        std::unique_ptr uptr1 = std::make_unique<A>();
        std::unique_ptr<A> uptr2(new A);
        uptr0.reset(a);  //the smart pointer uptr0 takes ownership over 'a' pointer
    }  // uptr1 and uptr2 will call their destructors here
    cout << "===After code block===" << endl;
    return 0;
}  // uptr0 will call his destructor for obj 'a' here. Object pointed by leaky_ptr will memory leak here.
```

### Member functions

| [(constructor)](https://devdocs.io/cpp/memory/unique_ptr/unique_ptr "cpp/memory/unique ptr/unique ptr")       | constructs a new `unique_ptr`  <br>(public member function)                                          |
| ------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| [(destructor)](https://devdocs.io/cpp/memory/unique_ptr/~unique_ptr "cpp/memory/unique ptr/~unique ptr")      | destructs the managed object if such is present  <br>(public member function)                        |
| [operator=](https://devdocs.io/cpp/memory/unique_ptr/operator= "cpp/memory/unique ptr/operator=")             | assigns the `unique_ptr`  <br>(public member function)                                               |
| **Modifiers**                                                                                                 |                                                                                                      |
| [release](https://devdocs.io/cpp/memory/unique_ptr/release "cpp/memory/unique ptr/release")                   | returns a pointer to the managed object and releases the ownership  <br>(public member function)     |
| [reset](https://devdocs.io/cpp/memory/unique_ptr/reset "cpp/memory/unique ptr/reset")                         | replaces the managed object  <br>(public member function)                                            |
| [swap](https://devdocs.io/cpp/memory/unique_ptr/swap "cpp/memory/unique ptr/swap")                            | swaps the managed objects  <br>(public member function)                                              |
| **Observers**                                                                                                 |                                                                                                      |
| [get](https://devdocs.io/cpp/memory/unique_ptr/get "cpp/memory/unique ptr/get")                               | returns a pointer to the managed object  <br>(public member function)                                |
| [get_deleter](https://devdocs.io/cpp/memory/unique_ptr/get_deleter "cpp/memory/unique ptr/get deleter")       | returns the deleter that is used for destruction of the managed object  <br>(public member function) |
| [operator bool](https://devdocs.io/cpp/memory/unique_ptr/operator_bool "cpp/memory/unique ptr/operator bool") | checks if there is an associated managed object  <br>(public member function)                        |
| **Single-object version**, `unique_ptr<T>`                                                                    |                                                                                                      |
| [operator*operator->](https://devdocs.io/cpp/memory/unique_ptr/operator* "cpp/memory/unique ptr/operator*")   | dereferences pointer to the managed object  <br>(public member function)                             |
| **Array version**, `unique_ptr<T[]>`                                                                          |                                                                                                      |
| [operator[]](https://devdocs.io/cpp/memory/unique_ptr/operator_at "cpp/memory/unique ptr/operator at")        | provides indexed access to the managed array  <br>(public member function)                           |

### Non-member functions

| [make_uniquemake_unique_for_overwrite](https://devdocs.io/cpp/memory/unique_ptr/make_unique "cpp/memory/unique ptr/make unique")<br><br>(C++14)(C++20)                                               | creates a unique pointer that manages a new object  <br>(function template)                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| [operator==operator!=operator<operator<=operator>operator>=operator<=>](https://devdocs.io/cpp/memory/unique_ptr/operator_cmp "cpp/memory/unique ptr/operator cmp")<br><br>(removed in C++20)(C++20) | compares to another `unique_ptr` or with `nullptr`  <br>(function template)                                                  |
| [operator<<(std::unique_ptr)](https://devdocs.io/cpp/memory/unique_ptr/operator_ltlt "cpp/memory/unique ptr/operator ltlt")<br><br>(C++20)                                                           | outputs the value of the managed pointer to an output stream  <br>(function template)                                        |
| [std::swap(std::unique_ptr)](https://devdocs.io/cpp/memory/unique_ptr/swap2 "cpp/memory/unique ptr/swap2")<br><br>(C++11)                                                                            | specializes the [`std::swap`](https://devdocs.io/cpp/algorithm/swap "cpp/algorithm/swap") algorithm  <br>(function template) |


