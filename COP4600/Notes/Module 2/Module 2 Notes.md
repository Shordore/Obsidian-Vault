<p style = "font-size: 30px;"> AI Summary:</p>

**Presentation 1: Introduction to Processes** 

**Key Topics:**

1. **Process Overview**:

• A **process** is a program in execution, not just the static program or algorithm. It includes the program plus the state (variables, counters, etc.).

• Memory structure of a process:

• **Text** (code), **Data** (constants and global variables), **Heap** (dynamic allocations), and **Stack** (local variables).

• The heap grows upward, and the stack grows downward.

2. **Process Model**:

• Processes are independent of each other, executing in their own “world.”

• The OS manages these processes, ensuring they don’t interfere with each other unless explicitly programmed to communicate.

3. **Pseudoparallelism**:

• The illusion of parallelism created by the OS when it rapidly switches between processes (time-sharing). Each process gets a quantum of CPU time.

4. **Process Creation and Termination**:

• **Creation**: System initialization (init), **fork** (cloning existing process), or batch jobs.

• **Termination**: Can be voluntary (e.g., normal exit or abnormal exit) or involuntary (e.g., fatal error, signal/kill from another process).

5. **Process Control Block (PCB)**:

• The PCB holds all information about a process, including registers, memory pointers, file descriptors, and process state.


**Presentation 2: Introduction to the Scheduler** 

**Key Topics:**

1. **The Scheduler**:

• The **scheduler** manages process execution, deciding which process gets CPU time and when.

• It handles scheduling after interrupts and balances the needs of processes to avoid starvation.

2. **Process States**:

• **Running**: Currently executing on the CPU.

• **Ready**: Runnable, but not currently executing.

• **Blocked**: Waiting for an external event (e.g., I/O).

• **Swapped out**: Process saved to secondary storage due to memory constraints.

3. **Context Switching**:

• A **context switch** happens when the OS replaces one process with another. This involves saving the current process’s state and loading the next process’s state.

• Context switches occur for several reasons, such as blocking (I/O), CPU sharing (quantum expiration), and hardware interrupts.

4. **Signals**:

• **Signals** are system calls used to pass messages between processes (e.g., termination signals).

• Some signals (e.g., SIGKILL) cannot be caught and will force process termination.


**Presentation 3: Introduction to Threads** 

**Key Topics:**

  

1. **What is a Thread?**:

• A **thread** is a lightweight part of a process with its own execution history (program counter and stack). Multiple threads share the process’s code, data, and heap but have separate register sets and stacks.

• Threads are used to improve efficiency by breaking down complex tasks and reducing memory usage.

2. **User-Space vs. Kernel-Space Threads**:

• **User-space threads**: Managed without kernel intervention, but all threads in a process share the same CPU core.

• **Kernel-space threads**: Managed by the OS, allowing for multi-core execution, but context switches are more expensive.

3. **Hybrid Threading**:

• A mix of user and kernel threads to balance memory efficiency and performance. While complex, hybrid threading can optimize specific use cases.

4. **Thread Benefits and Dangers**:

• **Benefits**: Lower memory cost, faster context switching, and reduced thread creation/destruction time.

• **Dangers**: Risk of **race conditions**, **data corruption**, and **lost data** due to shared memory access among threads.

5. **Inter-Process Communication (IPC)**:

• Two main strategies: **Shared Memory** (direct memory access, requires synchronization) and **Message Passing** (handled by the OS or libraries, avoids memory-specific issues).


<p style = "font-size: 30px;"> My Notes:</p>

