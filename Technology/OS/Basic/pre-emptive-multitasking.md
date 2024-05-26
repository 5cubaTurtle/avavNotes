#multiprocessing  #scheduler
![[scheduler-graph.png]]
When interrupt occurs, interrupt handler returns control of the core to the scheduler rather than the interrupted process. The scheduler then decides what OS code to run if any and what process to run next.

1. CPU receives interrupt
2. interrupt stores program counter (so the interrupted code could be resumed later)
3. interrupt invokes handler
4. handler saves rest of state of CPU for the process (so the interrupted process could be resumed later)
5. handler does its business (whatever the interrupted device needs)
6. handler invokes the scheduler
7. scheduler selects a process to run
8. scheduler restores the state of the CPU (restores the CPU registers as they were when that process was running)
9. scheduler jumps execution to that process

To ensure the scheduler gets to run on a regular basis to allocate CPU time among processes (whether any I/O devices need attention or not), a [[clock-device]] on the main board  is configured to send an interrupt on a regular basis (about every 10 or 20 milliseconds).

The simplest priority by which the scheduler decides which process to run is [[round-robin]], every process runs in it's turn.