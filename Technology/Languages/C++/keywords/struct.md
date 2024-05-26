```cpp
#include <cstdio>
using namespace std;

struct A {
    int ia;
    const char * sb = "";
    int ic;
};

int main() {
    A a;
    a.ia = 1;
    a.sb = "two";
    a.ic = 3;
    printf("ia is %d, sb is %s, ic is %d\n", a.ia, a.sb, a.ic);
    
    return 0;
}
```

### Data members
The only difference in struct as opposed to a [[class]] is that data members default to public-[[access]].

> [!NOTE] Good Practice
> Use struct if the structure will only have data members without functions.

**Good practice**
### initialization
[doc](https://en.cppreference.com/w/cpp/language/zero_initialization)
[SO initialization](https://stackoverflow.com/questions/61240589/how-to-initialize-a-struct-to-0-in-c)
The following will initialize the struct to default values:
```c++
T(); // for example `T t`;
T t = {};
T{};       (since C++11)
T t; // like the first example
```
#### zero-initialize
```cpp
 typedef struct // C-style typedef'ed struct
 {
     int num1 = 100;
     int num2 = -100;
     int num3;
     int num4 = 150;
 } data_t;

 // EXPLICITLY set every value to what you want!
 data_t d1 = {0, 0, 0, 0};
 // OR (using gcc or C++20 only)
 data_t d2 = {.num1 = 0, .num2 = 0, .num3 = 0, .num4 = 0};
```
- Use `memset()` to force all bytes to zero:
    ```cpp
     data_t d3;
     memset(&d3, 0, sizeof(d3));
    ```