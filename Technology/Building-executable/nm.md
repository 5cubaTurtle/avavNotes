list symbols from object files.

list symbols from object files:  `nm <object_file>`  

list the archive index table (list the symbols in its objects):
`nm -s <archiveName.a>`  

flags:
- `-D` for dynamic symbols. For shared libraries.
- `-g` Display only extern symbols.
- `-s` When listing symbols from archive members, include the index: a mapping (stored in the archive by ar or ranlib) of which modules contain definitions for which names.
- `-C` Demangle C++ symbols
  - C++ compiler mangles the names of functions and variable to differentiate them from various classes namespaces and function overloading and overriding.
