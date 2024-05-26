
To compile a .cpp object file using gcc:
```shell
g++ -c -o file.o file.cpp
gcc -c -o file.o file.cpp
clang++ -c -o file.o file.cpp
clang -c -o file.o file.cpp
```
- the `-c` flag indicates to stop at object creation. (without this flag g++ would proceed with linking and creating an executable)  
- `-g` gdb symbols for debbuging   


checking which compiler was used to compile:  `objdump -s --section .comment <file_name>`

Use [[ar]] to manage archives.
Use [[nm]] to explore object files.
Search for 'nm' in 'ar' man page for more info.

==warning:==
"nm" is aliased to something in the amdocs dev env!  
Use `'nm'` instead of `nm` this will disable the alias

To demangle a C++ symbol use: `c++filt`  
For example `c++filt _ZNSt8ios_base4InitC1Ev`  
yields: `std::ios_base::Init::Init()`  

ldd prints the shared libraries required by each program or shared library:  
`ldd <FILE>`

Links:
[yolinux libraries article](http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html)
