Constructors are always named as the class.
### Example code
```cpp
#include <cstdio>
#include <string>
using namespace std;

const string unk = "unknown";
const string clone_prefix = "clone-";

// -- interface --
class Animal {
    string _type = "";
    string _name = "";
    string _sound = "";
public:
    Animal();   // default constructor - takes no arguments
    Animal(const string & type, const string & name, const string & sound);
    Animal(const Animal &); // copy constructor
    Animal & operator = (const Animal &); // copy operator
    ~Animal();  // destructor
    
    void print() const;
};

// -- implementation --
Animal::Animal() : _type(unk), _name(unk), _sound(unk) {
    puts("default constructor");
}

Animal::Animal(const string & type, const string & name, const string & sound)
: _type(type), _name(name), _sound(sound) {
    puts("constructor with arguments");
}

Animal::Animal(const Animal & rhs) {
    puts("copy constructor");
    _name = clone_prefix + rhs._name;
    _type = rhs._type;
    _sound = rhs._sound;
}

Animal::~Animal() {
    printf("destructor: %s the %s\n", _name.c_str(), _type.c_str());
}

void Animal::print () const {
    printf("%s the %s says %s\n", _name.c_str(), _type.c_str(), _sound.c_str());
}

Animal & Animal::operator = (const Animal & rhs) {
    puts("copy operator");
    if(this != &rhs) {
        _name = clone_prefix + rhs._name;
        _type = rhs._type;
        _sound = rhs._sound;
    }
    return *this;
}

int main() {
    Animal a;
    a.print();
    
    const Animal b("cat", "fluffy", "meow");
    b.print();
    
    const Animal c = b;
    c.print();
    
    a = c;
    a.print();
    
    return 0;
}
```
### Initialization list
```cpp
Animal::Animal() : _type(unk), _name(unk), _sound(unk) {
```
### Default constructor
**default constructor** is a constructor that can be called with no arguments. It either takes no arguments or has default values for each of the arguments taken.
## Implicit constructors
_implicitly declared constructor_ which is a _default_ or copy constructor that will be declared for all user classes if no user defined constructor is provided (default) or no copy constructor is provided (copy). That is, a class with no constructors declared by the user has one _default constructor_ implicitly declared.
```cpp
class A {};
int main() {
    A a; //implicit constructor
    A b = a; //implicit copy-constructor
    a = b;  //implicit assignment operator
}  // here at the end of the block, the implicit destructor is used
```

[implicit vs default stackoverflow](https://stackoverflow.com/a/12340762)
#### Rule of 3
As implicit methods are provided for copy Ctor, assignment operator and Dtor. If you define any one of them, you probably should define all 3 of them.
[rule of 3/5/0](https://en.cppreference.com/w/cpp/language/rule_of_three)

### calls for constructors and assignment operator
```cpp
Str x1("llalal x1"); //Ctor
Str x2(x1);          //cCtor - copy constructor
Str x3= "bubub x3";  //Ctor + "invisible" cCtor - copy constructor (if either Ctor or cCtor is explicit or declared in private, this will not work)
Str x4= x1;  //cCtor - copy constructor (if cCtor (copy constractor) is explicit this will not work)
Str x5;     //Ctor
x5= x4;     //assignment operator =
Str x6;     //Ctor
x6="abcdefg x6";  //Ctor + assignment operator = (if Ctor is explicit this will stop working)
```