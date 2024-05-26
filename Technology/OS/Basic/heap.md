#memory #os #process 
Dynamically allocated memory of a process

Usually between the stack and the code sections. At the start of the process no heap is allocated. The process sends requests of heap to the OS. It specifies the size of requested memory. If it has enough contiguous heap memory available, the OS returns a pointer to the allocated memory. When the process does not need the allocated memory it should request the OS to deallocate it (with another syscall). The allocated chunks of memory are not necessarily adjacent. Although the OS manages the heap, over time, allocation and re-allocation of chunks of heap cause fragmentation of available heap memory. Effectively shrinking the size of chunks of memory which the OS can allocate because each chunk has to be contiguous.

##### memory leak
![video](https://youtu.be/9GDX-IyZ_C8?t=716)
![ggg](https://youtu.be/9GDX-IyZ_C8)


