
### Be careful with spaces
```cpp
#define F (x) x+1
```
Notice the unintentional space between `F` and `(` this will lead to an syntax error. F here is defined to `(x) x+1`, not what was intended by the programmer.
`F(3)` will give the following: `(x) x+1(3)`
### Parentheses
```cpp
#define ADD(a,b) ((a)+(b))
```
Note the parentheses a around the vars and the whole expression to avoid mixing order of operations with adjacent expression to the macro.
For example, if instead we define the same macro as:
```cpp
#define ADD(a,b) (a+b)
```
and then use it as follows:
```c
ADD(3,4-2)*8;
```
This will be evaluated to $3+4-2\cdot8=-9$ Instead of: $((3)+(4-2))\cdot8=40$
Conclusion - all of the parentheses are essentialr
### Rules of thumb
- macros should not be used on functions since they could be evaluated several times inside the macro.
- declarations of new variables should be avoided inside macros. This practice leads to errors in case we use the same macro in the same context (block) or could lead to name conflicts with other variables outside of macro.
- macros are not checked by compiler for syntax errors.
- when used with expressions with side effects, macros should be used with extra care.
- macros cannot be debugged.

### `#` operator:
`#x` makes the the string *x*. i.e `#` turns the symbols that follow it to string.
`y##x` makes the string *yx*. i.e concatenates the symbols to form a string.
