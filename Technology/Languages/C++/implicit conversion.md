### Example
Implicit conversion from *char* to *int*
```cpp
int i = 'x' // assigns ASCII value of 120 to i
```
or
```cpp
class I {
  public:
    int _i;
    I(int i): _i(i) {};
};

void func(const I& o) {
    std::cout << "got value:" << o._i << std::endl;
}

int main(){
    I e = 'z';  
	func('a'); // implicit conversion of argument to a function
}
```
Implicitly calls the [[Constructors|Ctor]] `I(int i)` with the parameter `i` as 122 - ASCII of *z*.
To prevent this behavior (at compile time) we could precede the Ctor with the [[explicit]] keyword.
```cpp
    explicit I(int i): _i(i) {};
```
