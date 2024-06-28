## Forward declaration
Forward declaration intended to inform the compiler about the existence of an identifier (class, function, variable) before its full definition is provided. This is useful when working with multiple source files or when you need to use an element from a class before its complete definition is available.
```cpp
class SomeClass;
```
#### Benefits of Forward Declarations:
- **Separate Compilation:** Enables you to compile multiple source files independently as long as they have forward declarations for any used elements defined in other files.
- **Circular Dependencies:** Helps break circular dependencies between classes. For example, if Class A has a member variable of Class B, and Class B has a member variable of Class A, forward declarations can prevent compilation errors by informing the compiler about their existence beforehand.
- You cannot use forward declarations for member functions within a class definition.
- Forward declarations only provide basic information about the identifier's existence and type. You cannot use the element until its full definition is available.

By effectively using forward declarations, you can improve code organization, facilitate separate compilation, and manage circular dependencies in your C++ projects.
## Range based for-loop
```cpp
std::vector<std::string> myVector = {"apple", "banana", "cherry"};
for (const std::string& element : myVector)
	std::cout << element << " ";  // Print each element directly
```

## Default Arguments
Could be used for functions or constructors.
```cpp
return_type function_name(parameter1, parameter2 = default_value2, ...);
```
- The caller can omit these arguments when calling the function, and the default values will be used.
- Default arguments must be placed at the end of the parameter list.

