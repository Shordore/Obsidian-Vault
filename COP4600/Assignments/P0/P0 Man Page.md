
.TH Project 0 "1" "09/09/24"
.SH NAME
COP4600 Project 0: My first kernel mod
.SH SYNOPSIS
The goal of this project is to introduce simple kernel modification techniques, and to get the student used to trolling file systems.
.SH DESCRIPTION
This project was fairly simple all in all. When I began I was unaware of the grep command, making the project significantly harder. After learning of it however, it became quite simple, and was a fun experience.
.PP
.IP "1."
.B grep -r "rcu_end_inkernel_boot()" .
.PP
I utilized this command to get a match on the file that calls this function as hinted at in the document. I found a match on a file with a file path of
.B /usr/rep/src/reptilian-kernel/init/main.c
.PP
I found the location in the file that referenced the function by doing a ctrl + w "where is" search
.PP
.IP "2."
.B printk(KERN_ALERT "\n##### Shahyah Darioosh (UFID: 1529-3266) This is a fun statement #####\n");
.PP
After the above step I placed a printk statement with a log level of alert as I experienced difficulty using KERN_EMERG where my vm would refuse to boot, forcing me to rollback to an earlier snapshot. With this finished I used the make, and sudo make install commands to rebuild my kernel, and rebooted my vm ensuring I took a screenshot of the text in the boot process.
.PP
.IP "3."
.B grep -r "20.0" .
.PP
Using this command I was able to get a hit on a file titled menu.lst
.PP
.B /mnt/sysroot/grub/menu.lst
After navigating to this file I placed my first and last name beside the default option.
I once again remade the kernel and took a screenshot during boot.
.PP
.IP "4."
I followed the commands given in the document to make the patch file.
.PP


.SH TESTING
I tested my patch file using a clean snapshot of the vm from before any modifications were made, and the patch properly applied the changes needed.
.PP
.SH BUGS
No known bugs.

.SH LINK
<span style="color: red;">Place Screencast link here</span>

.SH CITATIONS
https://man7.org/linux/man-pages/man1/grep.1.html

.SH Author
Shahyah Darioosh

