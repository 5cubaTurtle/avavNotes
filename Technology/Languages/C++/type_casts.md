
[cplusplus.com](http://www.cplusplus.com/doc/tutorial/typecasting/), [see also this](https://docs.oracle.com/cd/E19205-01/819-5267/bkahi/index.html)

### ﻿const_cast<>()
Manipulates the constness of the obj pointed by the pointer either to be set or removed. Note that removing the constness of an object and then writing to it causes undefined behavior.
### dynamic_cast<>()
Can only be used with pointers and references to classes (or with void*). Pointer upcasting (derived to base), in the same way as allowed as an implicit conversion. Pointer downcast (base to derived) polymorphic classes (classes with virtual members) if the potential obj is a valid complete obj of the target type (runtime checks are performed).  If downcasting from not a complete type, a NULL pointer is returned to indicate that, i.e. the compiler **checks** the content of the class the pointer points to before allowing the cast. Pointer of type Base which points to Base cannot be cast using `dynamic_cast<>()`to pointer of type Derived. However, pointer of type Base which points to Derived can be `dynamic_cast<>()` to pointer of type Derived.

### static_cast<>()
Conversions between pointers to related classes, not only upcasts but also downcasts without checks (thus no runtime overhead incurred by these checks). It has the same functionality as the dynamic_cast with less type-safety. It also deals with conversions between void* and other ptr types, between int, floating-point value, and enums. It can also: Call a single-argument Ctor or a conversion operator, convert to rvalue reference, converting any type to void, evaluating and discarding the value.

### reinterpret_cast<>()
Converts any ptr type to any other ptr type disregarding the pointer type and content pointed. Can also cast between ptr and int types, performing these casts usually makes the code non-portable.
