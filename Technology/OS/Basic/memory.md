#memory #os #process 
Processes also share the system's memory. The OS regulates processes use of memory to ensure each process does not interfere with other processes' or OS's memory. Each process can access only it's own portion of memory while the OS has access to all memory.
![[system-memory.png]]

This restriction is enforced by the hardware . Making it impossible for a process to muck with addresses outside of its own portion of memory.
There is a loophole for [[system-calls]] access. The addresses of system-calls are in OS's portion of memory and the process has to have access to it.

The [[CPU]] runs in two different privilege levels. When OS' code runs the [[CPU]] access to all memory unrestricted. When the process runs [[CPU]] put in a privilege level which triggers hardware exception when the code attempts to directly access I/O devices or addresses not allowed for that process.

#### Sections of process' memory
- call [[stack]], local variables, function execution.
- [[text]], code in binary form on a contiguous chunk of memory and never modified during the duration of the process except for the purpose of dynamic linking with [[shared-libraries]]. It usually stored in the opposite side to stack in virtual memory space. Meaning the stack grows towards the code section.
- [[heap]], dynamically allocated by syscalls.
![[memory-sections.png]]

#### Virtual memory
The memory addresses of a process do not refer to actual  bytes of system memory. Chunks of the process address space are mapped to chunks of system memory but not necessarily contiguously or in the same order.
![[memory-layout.png]]
When the OS runs a process, it lists these address mappings in a [[virtual-memory-table|table]]. The [[CPU]] consults this table to translate addresses of a process to addresses of actual [[RAM]].
Each process has its own complete address space. The OS keeps a separate [[virtual-memory-table|memory table]] for each process. Effectively, a process can be located by the OS in any part of [[RAM]], and each process can only access it's own memory. When a process attempts to use address space which is not mapped in it's table, the [[CPU]] triggers a HW exception. This typically causes the OS to abort the process with a "[[page]]-fault" error (the mapped chunks of memory are called [[page]]s). 