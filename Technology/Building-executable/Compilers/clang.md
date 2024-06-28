Clang LLVM compiler

[installation and uninstall](https://ubuntuhandbook.org/index.php/2023/09/how-to-install-clang-17-or-16-in-ubuntu-22-04-20-04/)

Syntax:`clang [options] file...`

C++ example: `clang++ main.cpp`
- `-o <output_file>` Name the output object file. Default is `a.out`
- `-std=c++17`  This specifies the C++ standard to be used during compilation. This enables features and syntax introduced in the C++17 standard.
- `-O3`  This option enables the third level of optimization. Optimization levels range from `-O0` (no optimization) to `-O3` (maximum optimization). The `-O3` level performs aggressive optimizations that can improve the performance of the generated code but may increase compilation time and the size of the executable. Specific optimizations at this level include [[inline|inlining]] functions, vectorization, unrolling loops, and more.
- `-DNDEBUG` This option defines the `NDEBUG` macro. When `NDEBUG` is defined, it disables the standard `assert` macro. This is typically used to remove debugging checks and assertions from the final build, which can improve performance. In production builds, it is common to define `NDEBUG` to ensure that no debug-only code is executed.

In my case I have to execute `clang++-18 -lstdc++` as the link to the *clang++* executable. See [clang++ vs clang StackOverflow](https://stackoverflow.com/a/20052006).
- `-lstdc++` link to standard c++ library. ([[g++]] does it by default)
- `clang++-18` specifies the version `18` to be used
- `-Wall` enables most of the commonly used warning messages.
- `-Wextra` additional warning messages not covered by `-Wall`. It catches even more potential issues and non-standard practices.
- `-Werror` all warnings are errors. i.e. will abort compilation.
	
### Setting Clang as Default Compiler (Optional)
If you want to make Clang your default compiler. Update your .bashrc or .zshrc file with:
```bash
export CC=clang
export CXX=clang++
```
Then reload the terminal configuration:
```sh
source ~/.bashrc 
```
This takes effect when compiling through [[Makefile]] 

### Production build
`clang++` `-std=c++17 -O3 -DNDEBUG`
 - `-03` highest optimization
 - `-DNDEBUG` disables debug checks