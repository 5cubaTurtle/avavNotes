### overloading example
Operator overloading example:
```cpp
#include <cstdio>
#include <iostream>
using namespace std;

class Rational {
    int _n = 0;
    int _d = 1;
public:
    Rational ( int numerator = 0, int denominator = 1 ) : _n(numerator), _d(denominator) {};
    Rational ( const Rational & rhs ) : _n(rhs._n), _d(rhs._d) {};    // copy constructor
    ~Rational ();
    int numerator() const { return _n; };
    int denominator() const { return _d; };
    Rational & operator = ( const Rational & );
    Rational operator + ( const Rational & ) const;  //the lhs
    Rational operator - ( const Rational & ) const;
    Rational operator * ( const Rational & ) const;
    Rational operator / ( const Rational & ) const;
};

Rational & Rational::operator = ( const Rational & rhs ) {
    if( this != &rhs ) {
        _n = rhs.numerator();
        _d = rhs.denominator();
    }
    return *this;  // reference to self
}

Rational Rational::operator + ( const Rational & rhs ) const {
    return Rational((_n * rhs._d) + (_d * rhs._n), _d * rhs._d);
}

Rational Rational::operator - ( const Rational & rhs ) const {
    return Rational((_n * rhs._d) - (_d * rhs._n), _d * rhs._d);
}

Rational Rational::operator * ( const Rational & rhs ) const {
    return Rational(_n * rhs._n, _d * rhs._d);
}

Rational Rational::operator / ( const Rational & rhs ) const {
    return Rational(_n * rhs._d, _d * rhs._n);
}

Rational::~Rational() {
    _n = 0; _d = 1;
}

// for std::cout
std::ostream & operator << (std::ostream & o, const Rational & r) {
    if(r.denominator() == 1) return o << r.numerator();
    else return o << r.numerator() << '/' << r.denominator();
}

int main() {
    
    Rational a = 7;        // 7/1
    cout << "a is: " << a << endl;
    Rational b(5, 3);    // 5/3
    cout << "b is: " << b << endl;
    Rational c = b;        // copy constructor
    cout << "c is: " << c << endl;
    Rational d;            // default constructor
    cout << "d is: " << d << endl;
    d = c;                // assignment operator
    cout << "d is: " << d << endl;
    Rational & e = d;    // reference
    d = e;                // assignment to self!
    cout << "e is: " << e << endl;
    
    cout << a << " + " << b << " = " << a + b << endl;
    cout << a << " - " << b << " = " << a - b << endl;
    cout << a << " * " << b << " = " << a * b << endl;
    cout << a << " / " << b << " = " << a / b << endl;
	
	b =  92 + b;  // Compilation error: error: invalid operands to binary expression ('int' and 'Rational')
    return 0;
}
```
### Class member operator overloads
Because the operator overloads are member functions they only need one argument - *lhs* of the operation is the object itself, thus not provided to the function, and the *rhs* is the argument (the operand). The assignment operator returns a reference to the existing object (*lhs*). The 4 last operators are [[const]]-safe since they return a new object.

### Non-member operator overloads
The overloading of the `<<` operator is done so it will be able to handle the `Rational` objects. This overload is not a member function of the class `Rational`, thus it needs a *lhs* argument in addition to *rhs*. It returns a `std::ostream` reference.
##### Example
The compilation error for the line `b = 92 + b;` could be fixed by overloading the `+` operator as a non-member function:
```c++
Rational operator + (const Rational& lhs, const Rational& rhs) {
   return (lhs.numerator()*rhs.denominator() + rhs.denominator()*lhs.numerator()) / (rhs.denominator() * lhs.denominator());
}   
```
With this overload, the compiler will be able to process the operation of *int* + *Rational* on the line `b = 92 + b;`. It will use [[implicit conversion]] to construct *Rational* out of 92, and then will use the overloaded operator to execute *Rational* + *Rational*.

### Conversion operator
[Tutorial](https://riptutorial.com/cplusplus/example/1828/conversion-operators)

The following could be applied to cast to any type, not just *string* as in this example:
```c++
Rational::operator std::string() const {
    if( _d == 1 ) return std::to_string(_n);
    else return std::to_string(_n) + "/" + std::to_string(_d);
}
```
With this overloading the following code compiles: 
```c++
Rational a = 7;
string s = "Chewawa ";
s += a;  // The object 'a' implicitly converted to a string
```

### ++ operator
The unary increment and decrement operators `++`/`--` overloaded example:
```c++
class num {
    int value = 0;
public:
    num( int x = 0 ) : value(x) {}
    int getvalue() const { return value; }
    void setvalue( int x ) { value = x; }
    num & operator ++ ();   // post-fix increment
    num operator ++ (int);  // The 'int' is purely to distinguish this signature from pre-fix. The dummy type is alwasy 'int' irrespective of the actual class.
    num & operator -- ();
    num operator -- (int);
};


// pre-increment
num & num::operator ++ () {
    cout << "pre-increment: ";
    value += 1;
    return *this;
}

// post-increment
num num::operator ++ (int) {
    cout << "post-increment: ";
    num temp = *this;  // because of the need for a temporary value, post increment is considered more expansive
    value += 1;
    return temp;
}

// pre-decrement
num & num::operator -- () {
    cout << "pre-decrement: ";
    value -= 1;
    return *this;
}

// post-decrement
num num::operator -- (int) {
    cout << "post-decrement: ";
    num temp = *this;
    value -= 1;
    return temp;
}

ostream & operator << (ostream & o, const num & n) {
    return o << (n.getvalue());
}

int main()
{
    num n(42);
    cout << "value is " << n << endl;
    cout << "value is " << ++n << endl;
    cout << "value is " << n << endl;
    return 0;
}
```

### new
To allocate dynamic memory for an object use the `new` operator:
```c++
int* i_ptr = new int;
int* iarray_ptr = new int[5];  // allocate array of 5 int objects
```
Delete the previous allocations to prevent memory leaks:
```c++
delete i_ptr;
delete[] i_ptr;
```

Of allocation failed, `new` will throw an exception and return a [[nullptr]]. If exception throwing is not a possibility, `nothrow` parameter could be passed to `new`:
```c++
c1* o1 = new(nothrow) c1;
if(o1 == nullptr) {
	puts("new c1 failed");
	return 1;
```
In this case the return pointer needs to be checked for `nullptr`.

### functor
A class which acts as a function, but has the ability to keep state:
```c++
class MultBy {
    int mult = 1;
    MultBy();
public:
    MultBy ( int n ) : mult(n) {}
    int operator() ( int n ) const { return mult * n; }  // Overloading the function operator
};

int main() {
    const MultBy times4(4);
    const MultBy times10(10);
    const MultBy times15(15);
    printf("times4(5) is %d\n", times4(5));  // 20
    printf("times4(15) is %d\n", times4(15));  // 60
    printf("times10(5) is %d\n", times10(5));  // 50
    printf("times10(15) is %d\n", times10(15));  // 150
    printf("times15(5) is %d\n", times15(5));  // 75
    printf("times15(15) is %d\n", times15(15));  // 225
    return 0;
}
```
