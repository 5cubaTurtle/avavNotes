
## Overriding (at run time)
In this example, the `Derived` class inherits from the `Base` class:
```c++
class Base {
public:
    void foo() { puts("Base::foo"); }
};

class Derived: public Base {
public:
    void foo() { puts("Derived::foo"); }
};
```

Then at use of these classes:
```c++
	Derived d;
	d.foo();    // "Derived::foo"
	
	Derived& drd = d;
	drd.foo();  // "Derived::foo"
	
	Base& brd = d;
	brd.foo();   // "Base::foo" Since the reference is of the Base class.
```

If in case of the last call, `brd.foo()`, the intention is to call the derived class' foo, declare the `Base::foo` `virtual`: 
```c++
virtual void foo() { puts("Base::foo"); }
```
This will allow the Derived's `foo` to *override* the Base's `foo`, and then `brd.foo()` will call the Derived foo. This is a case of *polymorphism*.

>[!Warning]
If a class has any virtual functions, it probably needs to have a virtual destructor. This is because if reference needs access to the logic of the derived class, it should have access to the derived destructor to be able to cleanup the derived class' data at the end of the lifretime of it's objects. Otherwise, only the base destructor will be called which creates a potential for a memory leak.

A derived class can use its own version of a base-function, I.e., it can override the [[virtual]] functions of its base class.
To call the overridden function of the base class use the namespace of the base class:
```c++
Animal::speak()
```

## Slicinig
If a function receives a base class but you pass a drive class to it by value, it will slice the derived out and call a [[Constructors|cCtor]] on its object creating only the base object ignoring the derived class. However, if you pass the derived object by reference, then this is a case of polymorphism. No new temporary objects inside the function will be created and function will refer to the virtual table to figure which functions to use, the functions of the derived or the base. For example if a pointer of base type points to a derived class, and we call a function which is defined only in the base class, then this function will be executed. However, if the function is virtual and its defined in the derived class, then the derived will be called.
