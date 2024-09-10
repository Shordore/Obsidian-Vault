.TH Exercise 1 "1" "09/09/24"
.SH NAME
COP4600 Exercise 1 The Command line
.SH SYNOPSIS
The goal of his exercise is to get the student used to the command line, and its associated commands.
.SH DESCRIPTION
This was a very straightforward assignment, I just followed the instructions on the assignment document.

.IP "1."

.B /home/reptilian/darioosh_shahyah
.PP
this directory was made in the reptilian folder with the format of my last, then first name.
I created this file using the mkdir command
.BR
.IP "2."
.B grep -r "android_dev" .
.PP
this command finds all files from current directory, which was kernel source, that contains the keyword given.
I found out about this command in discussion period.
.BR
.IP "3." 
.B grep -r "android_dev" . > output.txt
.PP
This command was used to the same effect as the first grep command, but this time to output the results to a text file.
.BR
.IP "4."
I took a screenshot of the directory /usr/rep/src/reptilian-kernel/drivers/usb/gadget as instructed
.BR
.IP "5."
I took a screenshot of the command grep -r "android_dev" . > output.txt and the contents of the directory /usr/rep/src/reptilian-kernel
.BR
.IP "6."
I moved the file "output.txt" to the directory I made in the first step located in /home/reptilian/
.BR
.IP "7."
.B tar -cvf ex1.tar darioosh_shahyah
.PP
I used this command to compress the directory I made in step 1 to a tar file
.BR
.IP "8."
.B gzip ex1.tar
.PP
I used this command to compress the tar file I made in the previous step to make it ex1.tar.gz

.SH TESTING
No testing was neccesary for this exercise.

.SH BUGS
No known bugs.

.SH LINK
No screencast for this exercise.

.SH CITATIONS
https://man7.org/linux/man-pages/man1/grep.1.html
.PP
https://man7.org/linux/man-pages/man1/tar.1.html
.PP
https://linux.die.net/man/1/gzip

.SH Author
Shahyah Darioosh

