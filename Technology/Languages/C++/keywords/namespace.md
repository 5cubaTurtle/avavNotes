[doc](https://en.cppreference.com/w/cpp/language/namespace)
Namespaces provide a method for preventing name conflicts in large projects.

Entities declared inside a namespace block are placed in a namespace scope, which prevents them from being mistaken for identically-named entities in other scopes.

Entities declared outside all namespace blocks belong to the _global namespace_. The global namespace belongs to the [global scope](https://en.cppreference.com/w/cpp/language/scope "cpp/language/scope"), and can be referred to explicitly with a leading `::`. While it has no declaration, the global namespace is not an [unnamed namespace](https://en.cppreference.com/w/cpp/language/namespace#Unnamed_namespaces).

Multiple namespace blocks with the same name are allowed. All declarations within these blocks are declared in the same namespace scope.

Typically, namespaces defined in header files along with [[class]] definitions that use them.

Examples:
### [using declaration](https://en.cppreference.com/w/cpp/language/namespace#Using-declarations)
6) [using-declaration](https://en.cppreference.com/w/cpp/language/namespace#Using-declarations): makes the symbol member-name from the namespace ns-name accessible for [unqualified lookup](https://en.cppreference.com/w/cpp/language/lookup "cpp/language/lookup") as if declared in the same class scope, block scope, or namespace as where this using-declaration appears.
Syntax:`using <ns-name> :: <member-name>;`
example:
```cpp
using std::cout;
```