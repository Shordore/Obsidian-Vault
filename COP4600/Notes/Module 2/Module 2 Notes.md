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
A process is neither an executable nor an algorithm
	Are both static

process is a program in execution

Process = program + state

Memory
	Heap
		contain data and text
		Grows upwards
		Dynamic Allocations
	Stack
		Contains data to return to a procedure call
		Contains local variables
	In-between there is empty memory space for the stack and heap to grow towards each other.

The Process Model
	Requires unique program counter
		at least one thread of execution
	Independence of execution
		does not depend on any other process that is executing unless with explicit communication
	OS maintains this model

Pseudoparallelism
	Each process gets their turn on the CPU
		Each get around 10 milliseconds
		Still holds true for multi-core processors
		Processes then give control back to the CPU to continue to the next process.
	How is it achieved?
		CPU registers hold state of process while executing
		After the quantum the OS suspends the process and saves it state to the process control block which is held in RAM
		Old systems ran the risk of running out of RAM for the process states.
		OS Scheduler runs and loads CPU registers with next process state.

Creation and Termination
	Processes are created by:
		init
		fork
	Processes are terminated by:
		Normal Exit
		Abnormal Exit
		Fatal Error
		kill via process
			Signal coming from another process to kill

PCB
	The PCB holds various things about a process
	Is about 1-4kiB
	Holds the following info
		Process table
		Register values
		Text pointer
		Data pointer
		Heap pointer
		Stack pointer
		Files
		Pipes
		Devices
	Some systems may have more than this

The Scheduler
	Part of the OS that handles process scheduling (🫨)
	Decides which process gets to run
	Scheduler responds to interrupts
	Balances needs of processes to avoid problems
		Starvation etc.


Who Schedules the scheduler
	1. OS enters kernel mode
	2. Old process is removed and memory stored
	3. New process loaded
	4. Scheduler sets alarm
	5. OS switches to user mode, and process is run
	6. When alarm sounds, OS interrupts process, and scheduler executed
	7. Cycle repeats Ad nauseam.


Process States
	1. Running, Ready, Blocked
		1. Executing Instructions
		2. Not currently running, but can
		3. Waiting on external event, has caused CPU to yield
	2. Swapped out & blocked & Swapped out & Ready
		1. Not in RAM waiting on external event
		2. Not in RAM ready to execute upon load
	3. Initializing, and Exiting
		1. Preparing process to run
		2. Shutting down- cleaning up

Process State Diagram
![[Pasted image 20241010220303.png]]


Context Switching
	Occur due to
		Blocking Operations
			I/O (Voluntary)
		CPU Yield Operations
			Sleep
		CPU Sharing
			Time has expired, or higher priority process first.
		Asynchronous Events (Involuntary)
			Hardware Interrupts
			Signals (Software Interrupts)
			Exceptions (Divide by zero etc.)
	The OS must:
		Store register values
		Track memory addresses
		Update process state


Handling Signals
	Kernel receives signal via system call
		Syscall flags the process on the PCB indicating there is a pending singnal
		When time comes to process to run, instead of running, the signal is killed
	If PCB has registered handler, the target signal is stored, and handler queued for execution
	If no registered handler, target process is eliminated
	Once handler/termination completes, normal function continues.

Signals
![[Pasted image 20241010221207.png]]


Threads
![[Pasted image 20241010221610.png]]
	A thread of execution is a part of a process that:
		Has its own execution history
			Program counter
			Stack\
	Elements that are unique to a process, but not a thread, include:
		Text (instructions)
		Data (Constants/statics, including global variables)
		Heap (Dynamic allocations)

What is in a thread?
	Process-Specific
		Address space
		Global varieties
		Open files
		Child processes
		Pending alarms
		Signals & handlers
		CPU accounting
	Thread-Specific
		Program counter
		Registers
		Stack
		Slate

Why are threads used?
	1. Avoid wasting memory on repeated info
	2. Break up complicated tasks in to simpler ones
	3. Improve efficiency

User-Space vs. Kernel-Space Threads
![[Pasted image 20241010222145.png]]

Hybrid Threading
	Mixes both user and kernel threads to get best of both worlds
	More complex to implement so it is best used as an optimization if necessary

Dangers of threads
	Corrupt data state
	Race conditions
	Lost data
	Duplicated data
	