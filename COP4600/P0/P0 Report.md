
Name: Shahyah Darioosh
UFID: 1529-3226

Screencast: here

In this project I completed both the boot message, and the GRUB modification for the extra credit. I approached this project very inefficiently at first by combing through the filesystem just exploring different directories I felt might contain the files I needed. Once I realized this approach would not be conducive to success, I turned to other means, namely, the "grep" command. I was not aware of this command before this project, but I have since come to appreciate its extreme usefulness. Using the command I searched up different variations of the text hints given in the project document. By searching up "rcu_end_inkernel_boot()", I got a hit on the file "main.c" held within the init folder in the Reptilian kernel. After searching through that document I discovered the area we were instructed to place the message. I used the "printk" command and "KERN_ERR" log leveling in order to print my message. 


GRUB
The GRUB menu modification was quicker for me to complete as I had already learned of the "grep" command, therefore, I immediately attempted that, and discovered the file located in "<span style="color: red;"> INPUT FOLDER NAME HERE </span>" It was as simple as accessing this file in nano, and adding my first and last name to the first option on the list.