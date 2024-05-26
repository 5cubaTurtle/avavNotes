Clang LLVM compiler

[installation and uninstall](https://ubuntuhandbook.org/index.php/2023/09/how-to-install-clang-17-or-16-in-ubuntu-22-04-20-04/)

Syntax:`clang [options] file...`

C++ example: `clang++ main.cpp`
	In my case I have to do `clang++-18 -lstdc++` as the link to the *clang++* executable
		- `-lstdc++` link to standard c++ library. ([[g++]] does it by default)
		- `-o <output_file>` Name the output object file. Default is `a.out`
	With warnings: `clang++-18 -lstdc++ -Wall -Wextra -Werror main.cpp`
		- `-Wall -Wextra` more warnings
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

[clang++ vs clang StackOverflow](https://stackoverflow.com/a/20052006)
