
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
		



