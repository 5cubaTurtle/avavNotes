GNU project C and C++ compiler
**Build order**: preprocessing, compilation, assembly and linking.

Options:
Many options have multi-letter names; therefore multiple single-letter options may not be grouped: `-dv` is very different from `-d -v`.
`-c` do not to run the linker
### Include path
Check include search paths of gcc : `echo | gcc -E -Wp,-v -`

### Cross-compilation
When cross-compiling use: `<machine>-gcc` or `<machine>-gcc-<version>`

## C++
To compile c++ programs, invoke GCC as `g++`

#### `-std=`
[SO question](https://stackoverflow.com/a/68545455/5273667) about compiling *c++20* support.
This option is used to specify the language standard. It controls which version of the C++ standard the compiler should follow.
`gnu++20`: This indicates the specific version of the C++ standard and additional GNU extensions. Here’s the breakdown:

- `c++20`: This specifies the C++20 standard, which includes several new features and improvements over previous standards, such as concepts, ranges, coroutines, and more.
- `gnu++`: This prefix means that in addition to the standard C++20 features, the compiler will also enable GNU extensions. These are non-standard extensions provided by GCC that can offer additional functionality and optimizations but may not be portable to other compilers.