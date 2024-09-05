
Instructions are executed via a three step cycle
![[Pasted image 20240827153139.png]]


In order for multiple programs to run pipelining can be used to intelligently execute multiple tasks in the same tick.
![[Pasted image 20240827153338.png]]
Minimizes Idle time of the CPU


As memory gets further away from the CPU, access time increases.
order of speed:
	Registers
	L1
	L2
	L3
	SDRAM
	SSD
	HDD


BIOS is considered Legacy (since 2017)
EUFI used for x86 and x64 now


The boot process (BIOS)
Execute BIOS drivers
POST
Find boot device stored in NVRAM
load boot in RAM
execute boot block from boot sector
run boot loader

UEFI = Unified Extensible Firmware Interface Standard
The boot process (EUFI)
Execute architecture firmware
execute EFI drivers
Find boot device via NVRAM
get boot loader from EFI partition

ARM does not have equivalent for EUFI

