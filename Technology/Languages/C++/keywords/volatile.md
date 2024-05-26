#c
The keyword `volatile` exists for specifying special treatment for volatile marked memory locations (for example: `volatile int x;`), specifically: 
1. The content of volatile variable are unstable (can change by means unknown to the compiler).
2. All writes, to volatile data are "observable" so they must be executed religiously. 
3. All operations on volatile data are executed in the sequence in which they appear in the source code. 

The first two rules ensure proper reading and writing and the third rule allows implementation of I/O protocols that mix input and output. This informally what C and C++ volatile guarantees.
