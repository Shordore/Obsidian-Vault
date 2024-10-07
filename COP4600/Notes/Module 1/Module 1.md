<p style = "font-size: 30px;"> AI Summary:</p>
**Presentation 1: Introduction to Operating Systems** 

**Key Topics:**

1. **Generations of Operating Systems**:

• _Generation 1 (1945-1955)_: Vacuum tubes, no OS, single program execution, programmers were also operators.

• _Generation 2 (1955-1965)_: Transistors and batch systems; OS started to emerge to manage job sequences.

• _Generation 3 (1965-1980)_: Integrated circuits and multiprogramming; introduction of timesharing systems.

• _Generation 4 (1980-present)_: Personal computers with GUIs and more advanced OS functionalities.

2. **Key OS Concepts**:

• OS as a **Resource Manager**: Manages processes, memory, I/O devices, and user interactions.

• OS as an **Extended Machine**: Provides an abstraction layer that simplifies user interaction with hardware.

3. **The Role of an OS**:

• **Processes**: A program in execution, managing states like memory and resources.

• **Jobs**: Tasks awaiting or in execution, often synonymous with processes but distinct in technical definition.

4. **Multi-Programming vs. Uni-Programming**:

• **Uni-programming**: Sequential task execution, CPU idle during I/O.

• **Multi-programming**: Parallel tasks managed by the OS, reducing CPU idle time.

  
**Presentation 2: Named Calls and System Resources** 

**Key Topics:**

1. **System Resources**:

• OS manages CPU time, memory, storage, and I/O devices to ensure smooth system operation.

2. **Files and Processes**:

• **Files**: Persistent data storage used for both user data and I/O device communication.

• **Processes**: A running program with associated resources, organized in trees and may contain threads for efficient execution.

3. **Procedure Calls**:

• **Procedure calls** are functions executed entirely in user space. When a procedure is called, it creates a stack frame, executes the function, and returns results. Procedures may pass variables by value, reference, or name.

4. **System Calls**:

• A **system call** involves a context switch to kernel mode. It handles protected actions like I/O operations. The process involves trapping into kernel mode and using a system call dispatcher to manage the request.

5. **POSIX System Calls**:

• Examples include fork(), waitpid(), execve(), and file operations like read(), write(), and open(). These are essential for process management and file handling in Unix-like systems.


**Presentation 3: Hardware Interrupts** 

**Key Topics:**

1. **Hardware Interrupts**:

• A mechanism by which hardware devices signal the CPU to pause its current execution and handle an event (e.g., I/O completion).

• The process involves the device sending an interrupt request (IRQ), and the interrupt controller coordinating the CPU’s acknowledgment and response.

2. **Interrupt Handling**:

• The steps involve stopping the current instruction, entering kernel mode, and running an interrupt service routine (ISR) to handle the event.

• Once the interrupt is handled, the system returns control to the process scheduler, which resumes normal execution.

3. **Interrupt Masks**:

• If an interrupt occurs while another is being processed, an interrupt mask can block it until the current one is completed. Multiple interrupts must be restored in the correct order after processing.

4. **Precise vs. Imprecise Interrupts**:

• **Precise Interrupts**: Treated between instructions, ensuring full execution of current operations.

• **Imprecise Interrupts**: May interrupt an ongoing instruction, which adds complexity but reduces wait time.

5. **Comparison of System Calls and Interrupts**:

• Both involve transitioning into kernel mode, but system calls are initiated by software (via a user program), while interrupts are hardware-initiated.


<p style = "font-size: 30px;"> My Notes:</p>

Algorithm
	A set of instructions with a finite initial store and state, with unambiguous ordering until the end.

Program
	Sequence of instructions that embody and algorithm

process
	A program in execution
	Program + process state (current instruction, state of memory/resources)

Job
	A task to be completed
	Often a program waiting for execution

![[Pasted image 20240829161203.png]]

Operating Systems act as a:
	Process Manager
	Memory Manager
	I/O Device

<p style = "font-size: 30px;"> File Systems</p>
	Give pattern to data on disk
	Have a specified mounting scheme
	Usually have naming and directory system
	Possibly have Redundancy and Networking
	Modern systems don't read directly from the disk

Naming Calls
	Procedure Calls
		Local Variables
		Pointer to entry/return
	System Calls
		Involves context switch into kernel mode
		Generally, there is a system library entry point
		



