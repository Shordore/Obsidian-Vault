
Found Sys call file at:
/usr/rep/src/reptilian-kernel/arch/x86/entry/syscalls/syscall_64.tbl
change after 434. Still have to figure out how to do that...

make 434-437 get, set, and proc(?) the log level.

/usr/rep/src/reptilian-kernel/kernel/sys.c

go here and add the int newloglevel = 0;
Also add all the syscalls needed.
make sure only root is allowed to set level
create syscall for invalid log levels (less than 0, greater than 7)
Switch case with log levels to print out message and PID.
process_log needs to have both header and c files finished

Checklist
-[x] Add 434-437 syscalls
-[x] Add get_proc_log_level definition
-[x] Add set_proc_log_level definition
-[x] Add proc_log_call definition
-[x] Add all 7 log levels according to spec in proc_log_call
-[x] finish process_log functions
-[] create Makefile


