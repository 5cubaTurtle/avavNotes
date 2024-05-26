Composition is used for objects that have a “**has-a” relationship** with each other. Therefore, the complex object is called the whole or a parent object whereas a simpler object is often referred to as a child object:
```c++
class A {};
class B {
A a;
};
```
Here *B* is composed from *A*.
