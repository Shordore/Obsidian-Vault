
Found Sys call file at:
/usr/rep/src/reptilian-kernel/arch/x86/entry/syscalls/syscall_64.tbl
change after 434. Still have to figure out how to do that...

make 434-437 get, set, and proc(?) the log level.

/usr/rep/src/reptilian-kernel/kernel/sys.c

go here and add the int newloglevel = 0;
Also add all the syscalls needed.
make sure only root is allowed to set level
create syscall for invalid log levels (less than 0, greater than 7)

Checklist
-[] Add 434-437 syscalls
-[] Add log level variable
-[] Add root check syscall
-[] Add invalid log level check
-[] Add all 7 log levels according to spec


