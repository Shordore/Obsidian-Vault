.TH Project 1 "1" "10/04/24"
.SH NAME
COP4600 Project 1: System Calls
.SH SYNOPSIS
The goal of this project is to teach students how to modify Reptilian to include three new system calls that can be used to log messages.
.SH DESCRIPTION
.PP
.IP "1."
.B /usr/rep/src/reptilian-kernel/arch/x86/entry/syscalls/syscall_64.tbl
.PP
I figured out where to go from watching Rohan's video. I followed his implementation. I modified this file in order to add 3 new system calls, their numbers, and names.
.PP
.IP "2"
.B /usr/rep/src/reptilian-kernel/include/linux/syscalls.h
.PP
I also found out where to go from Rohan's video and once again followed his implementation to write the syscall linkages. I modified this function in order to link together the .tbl functions I added to the definitions I wrote in sys.c
.PP
.IP "3"
.B /usr/rep/src/reptilian-kernel/kernel/sys.c
.PP
I found this file by following Rohan's video, and set up the "SYSCALL_DEFINE" based on the number of parameters for each function. I modified this file in order to actually write what I want to happen when my system calls are run.
.PP
.IP "4"
.B get_proc_log_level
.PP
I implemented this simply by returning the newLogLevel variable I created.
.PP
.IP "5"
.B set_proc_log_level
.PP
I implemented this by first comparing the current uid, to the root uid, and if they did not match, return -1. Similarly if the log level was out of bounds, below 0, or above 7, I returned -1. else the user is root and the log level is in bounds, I assigned the newLogLevel (which is the global variable) to the value on newLevel, and returned newLogLevel.
.PP
.IP "6"
.B proc_log_message
.PP
For this implementation I ensured the level was within range, and that level was less than or equal to the global log level, else i would return -1. I then implemented the 
.B copy_from_user
function in order to ensure the message is safely copied from the user space.
.PP
I then made a switch that takes the provided level, and based on that prints out the corresponding log level using printk. I got the executable number by adding current->comm, and got the PID by adding current->pid.

.SH TESTING
I tested my p1.diff file in a fresh kernel, and ensured it functionality. I also applied it using heartbeat-p1.sh to ensure it worked that way as well.
.PP
heartbeat-p1.sh was able to successfully compile my library, and I also did manual testing of it to ensure its functionality.
.PP

.SH BUGS
A couple of warnings, and a rare bug where compilation is not successful.

.SH LINK
https://youtu.be/q4XT8293zIo

.SH CITATIONS
Rohan, and Ernesto.
.PP
https://manpages.debian.org/testing/linux-manual-4.8/__copy_from_user.9.en.html
.PP
https://stackoverflow.com/questions/10838342/how-does-current-pid-work-for-linux
.PP
https://stackoverflow.com/questions/22346545/current-in-linux-kernel-code
.SH Author
Shahyah Darioosh
