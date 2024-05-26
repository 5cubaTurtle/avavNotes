## Example
```c++
// Animal class (base)
class Animal {
    string _name;
    const string _type;
    string _sound;
    // private constructor prevents construction of base class
    Animal(){}
protected:
    // protected constructor for use by derived classes
    Animal ( const string & n, const string & t, const string & s )
    : _name(n), _type(t), _sound(s) {}
public:
    void speak() const;
    const string & name() const { return _name; }
    const string & type() const { return _type; }
    const string & sound() const { return _sound; }
};

void Animal::speak() const {
    printf("%s the %s says %s\n", _name.c_str(), _type.c_str(), _sound.c_str());
}

// Dog class - derived from Animal
class Dog : public Animal {
    int _walked;
public:
    Dog( string n ) : Animal(n, "dog", "woof"), _walked(0) {};
    int walk() { return ++_walked; }
};

// Cat class - derived from Animal
class Cat : public Animal {
    int _petted;
public:
    Cat( string n ) : Animal(n, "cat", "meow"), _petted(0) {};
    int pet() { return ++_petted; }
};

// Pig class - derived from Animal
class Pig : public Animal {
    int _fed;
public:
    Pig( string n) : Animal(n, "pig", "oink"), _fed(0) {};
    int feed() { return ++_fed; }
};

int main() {
    Dog d("Rover");
    Cat c("Fluffy");
    Pig p("Arnold");
    
    d.speak();
    c.speak();
    p.speak();
    
    cout << "the " << d.type() << " has been walked " << d.walk() << " times" << endl;
    cout << "the " << c.type() << " has been petted " << c.pet() << " times" << endl;
    cout << "the " << p.type() << " has been fed " << p.feed() << " times" << endl;
}
```


## Member access specifiers
In the following example of inheritance the *access specifier* is public.
```c++
class Dog: public Animal {
...
}
```
The *access specifier* determines how the base class is inherited by the derived class. If no *access specifier* indicated, the inheritance will default to private and no public members will be available to the base class.
Access to a member is granted to an object under the following condition table:

|           | Base         | Derived      | Other Objects |
| --------- | ------------ | ------------ | ------------- |
| public    | $\checkmark$ | $\checkmark$ | $\checkmark$  |
| protected | $\checkmark$ | $\checkmark$ |               |
| private   | $\checkmark$ |              |               |

##  Overriding 
See [[Technology/Languages/C++/Polymorphism|Polymorphism]].

## friend
The `friend` declaration is used to grant access to private class members:
```c++
class Animal {
	friend class Dog;
	friend class Pig;
	friend const string& get_animal_name(const Animal&);
}
```
The classes *Dog* and *Pig* and the function *get_animal_name* are granted access to all privates of *Animal*.
>[!Note]
Accessor functions (interface methods) are preferred over be*friend*ing

## Multiple inheritance
Inheritance from more than one class.
```c++
class Cat: public Animal, public Fur {}
```
>[!Note]
>Generally [[Composition]] is preferred over inheritance and more so over multiple inheritance.
[Stack Overflow- Avoid inheritance](https://stackoverflow.com/a/407928)

## copy constructor of derived class
If a derived copy-Ctor (cCtor) defined, then we have to provide it with the Ctor for the base class. Example:
```cpp
class Base {
	Base(){}
	Base(const Base& other_){}
};

class Derived: public Base {
	Derived(){}
	Derived( const Derived& other_ ): Base(other_){}
};

int main() {
	Derived x;          //this will call the Base Ctor and then the Derived Ctor.
	Derived y(x);  
}
```
The expression `Derived y(x)`, will call the Base Ctor and then the Derived cCtor because while having the derived cCtor, the does not have the base cCtor, thus it creates new base object and then copies into it the derived object.
On the other hand, initializing the derived cCtor with a base cCtor like so: 
```cpp
Base(other_) 
```
inside the derived constructor will provide the cCtor of the derived class with a cCtor of the base. This will allow the creation of an exact copy of the derived. In the other case the base part of the copied object would be the default and not the copy of the base part of the y object.
