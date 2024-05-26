
### [10.3 Variables Used by Implicit Rules](https://www.gnu.org/software/make/manual/make.html#Implicit-Variables)

Here is a table of some of the more common variables used as names of programs in built-in rules:
`AR` Archive-maintaining program; default ‘ar’.
`AS` Program for compiling assembly files; default ‘as’.
`CC` Program for compiling C programs; default ‘cc’.
`CXX` Program for compiling C++ programs; default ‘g++’.
`CPP` Program for running the C preprocessor, with results to standard output; default ‘$(CC) -E’.
`FC` Program for compiling or preprocessing Fortran and Ratfor programs; default ‘f77’.
`M2C` Program to use to compile Modula-2 source code; default ‘m2c’.
`PC` Program for compiling Pascal programs; default ‘pc’.
`CO` Program for extracting a file from RCS; default ‘co’.
`GET` Program for extracting a file from SCCS; default ‘get’.
`LEX` Program to use to turn Lex grammars into source code; default ‘lex’.
`YACC` Program to use to turn Yacc grammars into source code; default ‘yacc’.
`LINT` Program to use to run lint on source code; default ‘lint’.
`MAKEINFO` Program to convert a Texinfo source file into an Info file; default ‘makeinfo’.
`TEX` Program to make TeX DVI files from TeX source; default ‘tex’.
`TEXI2DVI` Program to make TeX DVI files from Texinfo source; default ‘texi2dvi’.
`WEAVE` Program to translate Web into TeX; default ‘weave’.
`CWEAVE` Program to translate C Web into TeX; default ‘cweave’.
`TANGLE` Program to translate Web into Pascal; default ‘tangle’.
`CTANGLE` Program to translate C Web into C; default ‘ctangle’.
`RM`  Command to remove a file; default ‘rm -f’.

Here is a table of variables whose values are additional arguments for the programs above. The default values for all of these is the empty string, unless otherwise noted.
`ARFLAGS` Flags to give the archive-maintaining program; default ‘rv’.
`ASFLAGS` Extra flags to give to the assembler (when explicitly invoked on a ‘.s’ or ‘.S’ file).
`CFLAGS` Extra flags to give to the C compiler.
`CXXFLAGS` Extra flags to give to the C++ compiler.
`COFLAGS` Extra flags to give to the RCS co program.
`CPPFLAGS` Extra flags to give to the C preprocessor and programs that use it (the C and Fortran compilers).
`FFLAGS` Extra flags to give to the Fortran compiler.
`GFLAGS` Extra flags to give to the SCCS get program.
`LDFLAGS` Extra flags to give to compilers when they are supposed to invoke the linker, ‘ld’, such as -L. Libraries (-lfoo) should be added to the LDLIBS variable instead.
`LDLIBS` Library flags or names given to compilers when they are supposed to invoke the linker, ‘ld’. LOADLIBES is a deprecated (but still supported) alternative to LDLIBS. Non-library linker flags, such as -L, should go in the LDFLAGS variable.

### sample Makefile
```make
.PHONY: all-packages  
all-packages: packages  
@echo RSROSSERIAL=$(RSROSSERIAL)  
@echo ROBOCLAW_RS=$(ROBOCLAW_RS)  
cd $(RSROSSERIAL) && make package  
cd $(ROBOCLAW_RS) && make package  
```

1. `.PHONY: all-packages`: This line declares the target "all-packages" as a phony target. Phony targets are targets that do not represent actual files but rather serve as a way to group other targets or provide convenient commands. In this case, "all-packages" is declared as a phony target to indicate that it doesn't correspond to a file.
2. `all-packages: packages`: This line specifies that the target "all-packages" depends on the target "packages". It means that before executing the commands associated with the "all-packages" target, the "packages" target needs to be executed.
3. The lines starting with `@echo` are used to print the values of certain variables. They are preceded by the `@` symbol, which suppresses the printing of the command itself.
4. The subsequent `cd` commands change the working directory to the specified paths using the variables `RSROSSERIAL`and `ROBOCLAW_RS`. The `$(variable_name)` syntax is used to expand the values of the corresponding variables.
5. Within each directory, the command `make package` or `make packages` is executed. This invokes the Makefile in the respective directory and executes the target "package" or "packages" defined in those Makefiles.

### stop execution if error encountered
By default, if one of the commands in a Makefile fails (i.e., returns a non-zero exit status), the execution of the remaining commands will be aborted. This behavior is due to the default error handling mechanism in Make.

In the provided Makefile, if any of the `cd $(directory) && make package` or `cd $(directory) && make packages` commands fails, the execution will halt, and the subsequent commands will not be executed.
This behavior can be modified or overridden by explicitly instructing Make to ignore errors or continue executing the subsequent commands using special syntax or flags.

### Search path
Add a directory to the include search path:
	after the line obj-m = sgw.o, add the line:
	`EXTRA_CFLAGS=-I/usr/include/x86_64-linux-gnu/ -I/usr/include`
	here I added 2 directories (*../x86_64-linux-gnu* and */usr/include*) to the default include search path