
### Item 2: const (constexpr - might be better than the advice here)
Prefer `const`s, `inline`s, and `enum`s to `#defines`.

`#defines` are not known to the compiler (it's not in it's symbol table), hence it can't generate informative error messages about them, making debugging a headache. Furthermore, example:
	`#define RATIO 1.653`
	This will replace all `RATIO`'s in your code with *1.653*. This could result in multiple copies of *1.653*. Instead use:  `const double 1.653;`.This will never result in more than one copy.

When defining constant ptrs in headers files, make sure both are `const` the ptr and the pointed value:
	`const char* const authorName= "ScottMeyers";`

Furthermore std::string objects are more preferable to `char*`. Thus:
	`const std::string authorName("ScottMeyrers"); `

Defining const's inside class, make sure its static to prevent each obj creating its own const value:
```c++
class GamePlayer {
private:
	static const int NumTurns = 5;
	int scores[NumTurns];
	...
};
```

- Above is a constant _declaration_ for NumTurns, not a definition. The compiler might incorrectly require you to define them, then use:
    `const int GamePlayer::NumTurns;`. No value is given because initial value of const is provided at declaration
Notice: this goes into .cpp file not .hh.
- Or use the enum hack:
```c++
class GamePlayer {
private:
     enum { NumTurns = 5 }; // “the enum hack” — makes NumTurns a symbolic name for 5
     int scores[NumTurns];       // fine
     ...
};
```
It's not possible to take the address of enum (sometimes its a good thing).

- Macros: Use inline template functions instead of macro functions. Functions obey scope and less buggy.

### Item 3: Use const whenever possible
- When using STL containers: When creating an iterator which points to a value that should be const use:
```c++
std::vector<T>::const_iterator cIter= vec.begin();  //cIter acts like const T* (the data cannot be changed)
```

- Sometime have a function return const:
```c++
class Rational { ... };
const Rational operator*(const Rational& lhs, const Rational& rhs);
```
This prevents bugs like:
- `(a * b) = c;`    invoke operator=
- `if (a * b = c) ...`     oops, meant to do a comparison!

User defined types should avoid gratuitous incompatibilities with the built-ins (for example allowing assignment to result of a product operation).
- When overloading `operator[]` always consider overloading the `const operator[]`.
- Use the `mutable` keyword: allows const member functions to modify data member
