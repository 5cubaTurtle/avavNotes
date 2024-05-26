
```cpp
class A {
    int _value = 0;
public:
    void setv ( const int a ) { _value = a; };
//    void setv ( const int a ) const { _value = a; }; //const setter which will fail at compilation

    int getv () { cout<<"mutable getter "; return _value; };
    int getv () const { cout<<"const getter "; return _value; };
};

int main() {
    A a;
    a.setv(42);
    std::cout << "a is " << a.getv() << endl;
    
    const A b = a;
    std::cout << "b is " << b.getv() << endl;
return 0;
}

```
- [[const]] in `setv()` means the passed parameter will not be written to, i.e. a new value will not be assigned to it.
- [[const]] in `getv()` means state of the object (of this class `A`) will not be changed by this function. i.e. member variables will not be written to.
- `b.getv()` will not compile without the `const` qualifier in the signature of the function. It will give the following error:
```sh
member-function.cpp:23:29: error: 'this' argument to member function 'getv' has type 'const A', but function is not marked const
   23 |     std::cout << "b is " << b.getv() << endl;
```
Since the object `b` is qualified as `const` it can only call `const` qualified functions.