A system call is a routine by which a process initiate a request to the OS.
A system call provides HW related functionality to the process like file-I/O or sending/receiving data over the network.

A specific CPU instruction in which the process specifies a system-call number. When the instruction is invoked the CPU look in the syscall table corresponds with the number and jumps execution to that address.