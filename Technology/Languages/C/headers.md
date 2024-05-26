The pre-processor directives are the files which are processed when we compile the program. A directive could be called upon by a *header* in the following manner, for example:
`#include <stdio.h>`
this line, at the start of our program, includes the file *stdio.h* which is located at the default directory indicated by the triangular brackets (`<>`).
### Defining [[Technology/Languages/C/Macros|Macros]]
`#define CONSTANT 65` 
Defining this macro willl force the linker to substitute *65* for every *CONSTANT* it encounters in the code.
### Creating a header file
Create a file with an ending of *.h* (header). for example create a file named *newfile.h*. This file could be included in our program as follows:
`#include "newfile.h"`
This inclusion will allow the program to use any constants or functions from the *newfile.h* file.
Since the name of the header file - *newfile.h* is wrapped inside quotations (`"`), this means the location of the file is in the same directory as our program file.