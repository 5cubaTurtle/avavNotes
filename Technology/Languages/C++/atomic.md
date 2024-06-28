Operation that is performed in a way that is indivisible and uninterruptible to prevent race condition.
No other thread can observe the operation in an incomplete state.

- **Atomic Variables**: Modern C++ provides atomic variables via the `<atomic>` header. These variables support atomic operations like load, store, fetch-and-add, compare-and-swap, etc.
- **Lock-Free Operations**: Operations on atomic variables that do not require locks to ensure atomicity. These operations are guaranteed to be atomic by the hardware.
- **Avoids Deadlocks**: Since atomic operations don't involve locking mechanisms, they can avoid complex deadlock scenarios that are common with mutexes and other locks.

### Examples:  
  - **Declaration**:
  ```cpp
  #include <atomic>
  
  std::atomic<int> atomicCounter(0);
  atomicCounter++;
  ```
- **Load and Store**:
  ```cpp
  std::atomic<int> atomicVar;
  atomicVar.store(10); // Atomic store
  int value = atomicVar.load(); // Atomic load
  ```

- **Fetch-and-Add**:
  ```cpp
  std::atomic<int> atomicCounter(0);
  int oldValue = atomicCounter.fetch_add(1); // Atomically increment by 1
  ```

- **Compare-and-Swap (CAS)**:
  ```cpp
  std::atomic<int> atomicValue(0);
  int expected = 0;
  int newValue = 1;
  bool success = atomicValue.compare_exchange_strong(expected, newValue); 
  // If atomicValue is equal to expected, it is replaced with newValue
  // success is true if the exchange happened
  ```
### Hardware Support:
Atomic actions are often supported directly by hardware, providing mechanisms such as atomic instructions that ensure operations on specific memory locations are atomic. Examples include the `LOCK` prefix in x86 assembly or specific atomic instructions in ARM architecture.

## Atomic operations are more expansive than non atomic
Yes, atomic actions are generally more expensive than regular actions, but the degree of expense can vary depending on several factors such as the specific operation, the hardware architecture, and the system's current load. Here are some reasons why atomic actions tend to be more costly:

### Reasons for Increased Cost:
1. **Hardware Synchronization**:
   - Atomic operations often require special hardware instructions that ensure the operation is completed without interruption. These instructions can involve memory fences, cache synchronization, and other mechanisms that enforce atomicity.
   - On many architectures, atomic instructions may lock the memory bus or specific cache lines, ensuring exclusive access during the operation. This can temporarily block other operations, reducing overall throughput.

2. **Memory Ordering**:
   - Atomic operations may include memory ordering constraints to prevent reordering of instructions around the atomic operation. Ensuring these constraints can add overhead.
   - Operations like `compare-and-swap` (CAS) or `fetch-and-add` often require multiple memory accesses (e.g., reading and conditionally writing) which can be slower than a single read or write operation.

3. **Cache Coherency Protocols**:
   - Maintaining cache coherency for atomic operations can be expensive. The hardware needs to ensure that the atomic operation is visible to all processors in a consistent manner, which may involve invalidating cache lines or transferring data between caches.

4. **Contention**:
   - When multiple threads frequently access the same atomic variable, contention can occur, leading to performance degradation. The cost of resolving this contention (e.g., retrying CAS operations) adds to the overall expense.

### Example of Cost Comparison:
Consider incrementing an integer in a multi-threaded environment:
- **Regular Increment** (non-atomic):
  ```cpp
  int counter = 0;
  void increment() {
      counter++; // Not safe in multi-threaded context
  }
  ```
  - This is a simple read-modify-write operation that is very fast in a single-threaded context.
  
- **Atomic Increment**:
  ```cpp
  std::atomic<int> atomicCounter(0);
  void atomicIncrement() {
      atomicCounter++; // Safe in multi-threaded context
  }
  ```
  - This involves hardware-level atomic instructions to ensure the operation is thread-safe, which is inherently slower than a non-atomic increment due to the reasons mentioned above.

### Practical Considerations:
- **Necessity vs. Cost**:
  - While atomic operations are more expensive, they are essential for correctness in concurrent programs where race conditions must be avoided.
  - The additional cost is justified by the guarantee of correctness and safety in a multi-threaded environment.

- **Performance Tuning**:
  - In performance-critical applications, it's important to balance the use of atomic operations with other synchronization mechanisms (like mutexes) and consider alternative designs to minimize contention and the frequency of atomic operations.
  - Profiling and benchmarking can help identify bottlenecks and determine the optimal synchronization strategy.

### Conclusion:
Atomic actions are generally more expensive than regular actions due to the additional overhead of ensuring atomicity and memory consistency. Despite the higher cost, they are crucial for maintaining correctness in concurrent programming. Developers should use atomic operations judiciously, considering both performance implications and the need for safe multi-threaded access to shared resources.
## atomic vs mutex
Yes, atomic actions are generally more expensive than regular actions, but the degree of expense can vary depending on several factors such as the specific operation, the hardware architecture, and the system's current load. Here are some reasons why atomic actions tend to be more costly:

### Reasons for Increased Cost:
1. **Hardware Synchronization**:
   - Atomic operations often require special hardware instructions that ensure the operation is completed without interruption. These instructions can involve memory fences, cache synchronization, and other mechanisms that enforce atomicity.
   - On many architectures, atomic instructions may lock the memory bus or specific cache lines, ensuring exclusive access during the operation. This can temporarily block other operations, reducing overall throughput.

2. **Memory Ordering**:
   - Atomic operations may include memory ordering constraints to prevent reordering of instructions around the atomic operation. Ensuring these constraints can add overhead.
   - Operations like `compare-and-swap` (CAS) or `fetch-and-add` often require multiple memory accesses (e.g., reading and conditionally writing) which can be slower than a single read or write operation.

3. **Cache Coherency Protocols**:
   - Maintaining cache coherency for atomic operations can be expensive. The hardware needs to ensure that the atomic operation is visible to all processors in a consistent manner, which may involve invalidating cache lines or transferring data between caches.

4. **Contention**:
   - When multiple threads frequently access the same atomic variable, contention can occur, leading to performance degradation. The cost of resolving this contention (e.g., retrying CAS operations) adds to the overall expense.

### Example of Cost Comparison:
Consider incrementing an integer in a multi-threaded environment:
- **Regular Increment** (non-atomic):
  ```cpp
  int counter = 0;
  void increment() {
      counter++; // Not safe in multi-threaded context
  }
  ```
  - This is a simple read-modify-write operation that is very fast in a single-threaded context.
  
- **Atomic Increment**:
  ```cpp
  std::atomic<int> atomicCounter(0);
  void atomicIncrement() {
      atomicCounter++; // Safe in multi-threaded context
  }
  ```
  - This involves hardware-level atomic instructions to ensure the operation is thread-safe, which is inherently slower than a non-atomic increment due to the reasons mentioned above.

### Practical Considerations:
- **Necessity vs. Cost**:
  - While atomic operations are more expensive, they are essential for correctness in concurrent programs where race conditions must be avoided.
  - The additional cost is justified by the guarantee of correctness and safety in a multi-threaded environment.

- **Performance Tuning**:
  - In performance-critical applications, it's important to balance the use of atomic operations with other synchronization mechanisms (like mutexes) and consider alternative designs to minimize contention and the frequency of atomic operations.
  - Profiling and benchmarking can help identify bottlenecks and determine the optimal synchronization strategy.

### Conclusion:
Atomic actions are generally more expensive than regular actions due to the additional overhead of ensuring atomicity and memory consistency. Despite the higher cost, they are crucial for maintaining correctness in concurrent programming. Developers should use atomic operations judiciously, considering both performance implications and the need for safe multi-threaded access to shared resources.


## SO Question
In connection with multi-threading, [this](https://stackoverflow.com/q/70053971/5273667) SO question needs a better answer.
This can be answered better by comparing move and copy operations in the context of several threads that do some work (maybe sorting words in a randomized dictionary).