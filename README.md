# OverTheWire-Walkthrough

## Introduction

Here's a quick write-up of the OverTheWire bandit wargame (https://overthewire.org/wargames/bandit/). All levels will be included. For those that don't want to be spoiled, I will give few hints before digging deep into the level.
Also, don't forget to create a password file containing all the passwords you fought. It's a hassle to go back at level 0 when you were level 10 because your PC shut down for example.


### Level 0
Level Goal :
*The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.*

So first of all, we will be using SSH in order to connect to the host on port 2220. Here's the command line :
![bandit0](https://github.com/user-attachments/assets/6375267d-5cbd-47b7-87a9-ac3aa5666f6a)

In order to connect to a SSH we use this topology : ``username@IP_ADRESS`` or ``username@DOMAIN_NAME``. Since they gave us the username, domain name and also the password, we can confidently write it like this : ``bandit0@bandit.labs.overthewire.org`` . If you don't specify the port, it will automatically try to connect to the port 22 and it will give us an error. This is why ``-p 2220`` is important. Lastly, don't forget to invoke ``sudo``.

If it worked, you should see this. Simply type the password they gave us : 
![bandit0_1](https://github.com/user-attachments/assets/fc03a610-4c7a-4371-bbc4-7c793ca4fc86)


This will lead us to be on the bandit0 machine, which should be like this :
![bandit0_2](https://github.com/user-attachments/assets/8114d81e-9426-45f7-8ae5-e60868272aa8)

Bravo ! This one was fast and easy but still ! You completed your first bandit level ! Don't forget to **save** the **password** in your password file also.


### Level 0 - 1
*Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.*

*Commands you may need to solve this level :*
**ls , cd , cat , file , du , find**

*Note : You wouldn't be able to hop from level to level using SSH from another SSH session. You need to connect to a level using your own root machine and not the bandit one !!*

We have now access to the bandit0 machine, let's **ls** in order to discover what is in there. **ls** can let us see the content of a directory.
![bandit0_3](https://github.com/user-attachments/assets/b4f322f4-3130-4aee-9902-3c4a645504a0)

Bingo ! Now we just have to open this file using **cat**  . **cat** let us print the file in a standard output.
![bandit0_4](https://github.com/user-attachments/assets/f231de29-4f69-432f-bb37-f5df93691621)


### Level 1 - 2

*Level Goal :
The password for the next level is stored in a file called - located in the home directory*

Commands you may need to solve this level :
**ls , cd , cat , file , du , find**


Ok, so first of all, if you have trouble login in to this level, don't forget that the SSH username is now bandit1 for the level 1-2, and bandit2 for the level 2-3, and so on..

Now, we need to  find and open the "-" directory. So we find the "-" directory by using ``ls``, then we use ``cat`` again but we have a problem when we do that :
![bandit1](https://github.com/user-attachments/assets/9721cbe6-6bcb-41ea-893b-9d393e244b8b)


Indeed, bash doesn't understand that we want to see the file since it is called like that. A little trick that we can do is to put ``./`` before the directory name so it can get understand by BASH just like that :
![bandit 1_1](https://github.com/user-attachments/assets/89cbec04-51ce-4e9a-b8a9-502d2fe05008)


Yessir ! Let's move on !

### Level 2 - 3
*Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory*

Commands you may need to solve this level
**ls , cd , cat , file , du , find**

In this level, we need to find a file and open it. Let's do that.
I will ``ls`` then open the file using ``cat`` but as soon as I do it, it gave me this :
![bandit2](https://github.com/user-attachments/assets/da9d486d-fa1a-48d1-9367-45d838dc5755)


Ok so this is why you don't name a file that has spaces without using underscore or some other stuff. Got it. Let's find how to open it.

In this article (https://linuxhandbook.com/filename-spaces-linux/) we can see that by wrapping the whole name, you can open it (Example : cat "spaces in this filename") . Let's see if it work :
![bandit2_1](https://github.com/user-attachments/assets/ac150399-82c8-4110-aaa8-be65bb6002f4)


Great ! That was easier than I thought ! There was also another way to open it, using backslashes (Example : cat spaces\ in\ this\ filename) but I find it harder to type. Still good to know.



### Level 3 - 4

*Level Goal
The password for the next level is stored in a hidden file in the inhere directory.*

Commands you may need to solve this level
**ls , cd , cat , file , du , find**

An hidden file ? I have the perfect command for that : ``ls -la`` .

![bandit3](https://github.com/user-attachments/assets/93e5737d-ebc2-4b4f-9627-b7f8c337e07c)


the : ``-a`` argument in ls show us the hidden file in a directory. It is useful and should be learned by everyone. Anyway, let's ``cat`` this file :

![bandit3_1](https://github.com/user-attachments/assets/162f1d8e-6e00-44af-bf9e-528a7ad3406b)


Yes sir ! Let's see what's next.


### Level 4 - 5
*Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.*

Commands you may need to solve this level
**ls , cd , cat , file , du , find**

Alright. So in this level I have to find the only human-readable file in the directory. I wanted to know, first, if you could manually **cat** every file, which you can do. I find the password like that ! :

![bandit4](https://github.com/user-attachments/assets/2e5ddaf4-6e5d-4e58-a238-e1949ac40e87)


However, I do not think it was intended to be the primary source of finding, so I made some research in order to know how to do it using the command ``find`` . After few minutes, I came to something : ```find /path/to/search -type f -exec file {} + | grep ": text"```
In this one, ``find .`` means it search from the directory we are, ``-type f`` means that it searchs for files. ``-exec file {} +`` open every file during the search.`` grep text`` is a command that search for specific name (here, only text so human readable file).
Let's try it :

![bandit4_1](https://github.com/user-attachments/assets/a6007787-eee3-4528-b42a-23c16fb48417)


Indeed it worked ! 



### Level 5 - 6
Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable
Commands you may need to solve this level
ls , cd , cat , file , du , find

Alright, so this level is quite similar to the level 4-5 as we had to find a human readable file. Now we also need it to be not executable and 1033 bytes in size. The 1033 bytes can be formulate like this ``-size 1033c`` , not executable is written like that : ``! -executable`` so we should get something like that : ``find . -type f -size 1033c ! -executable -exec file {} +  | grep "text" `` . Let's try it !
![bandit5](https://github.com/user-attachments/assets/3a3f25d0-e879-44a7-af09-7cd689faf2e2)

Ok, it seems like it did worked. We have a file that is human readable (ASCII or UTC text), has 1033 bytes but is not a executable file. Let's **cat** this :

![bandit5_1](https://github.com/user-attachments/assets/bfd14b94-52b0-4d40-9dab-bfec1105191f)



### Level 6 - 7
The password for the next level is stored **somewhere on the server** and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size
Commands you may need to solve this level
ls , cd , cat , file , du , find , grep

Okay, so this is something I don't know. Im suspecting that the fact they bold **somewhere on the server** is that it can be related to a path or a file where the server should be. We can find it by specifying the group and the user + his size.  I think I'll go with what I learned in those precedent levels using ``find`` such as : ``find / -type f -group bandit6 -user bandit7 -size 33c -exec file {}+``
![bandit6](https://github.com/user-attachments/assets/5b3661f4-7db6-420c-82ae-9e386eadcb8f)

I specifically used ``find /`` to search in all of the files the device has since I wasn't really sure where the server files were. Also if it returned more than one query, I would've probably change my find method !

![bandit6_1](https://github.com/user-attachments/assets/465cc43b-75d5-4d5f-98e5-d8e1dd045dcc)


Fortunately I did find it pretty easily ! let's **cat** it !






### Level 7 - 8
Level Goal
The password for the next level is stored in the file data.txt next to the word millionth

Commands you may need to solve this level
man, grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

### Level 8 - 9

Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd


### Level 9 - 10
Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd


### Level 10 - 11
Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data

Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd



### Level 11 - 12
Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd


### Level 12 - 13
Level Goal
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file


### Level 13 - 14
Level Goal
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

Commands you may need to solve this level
ssh, telnet, nc, openssl, s_client, nmap


### Level 14 - 15
Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

Commands you may need to solve this level
ssh, telnet, nc, openssl, s_client, nmap


### Level 15 - 16
Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

Commands you may need to solve this level
ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss


### Level 16 - 17
Level Goal
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

Commands you may need to solve this level
ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss


### Level 17 - 18

Level Goal
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

Commands you may need to solve this level
cat, grep, ls, diff

### Level 18 - 19
Level Goal
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

Commands you may need to solve this level
ssh, ls, cat


### Level 19 - 20
Level Goal
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

### Level 20 - 21
Level Goal
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think

Commands you may need to solve this level
ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z, …)


### Level 21 - 22

Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

Commands you may need to solve this level
cron, crontab, crontab(5) (use “man 5 crontab” to access this)

### Level 22 - 23
Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

Commands you may need to solve this level
cron, crontab, crontab(5) (use “man 5 crontab” to access this)

### Level 23 - 24
Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

Commands you may need to solve this level
chmod, cron, crontab, crontab(5) (use “man 5 crontab” to access this)

### Level 24 - 25
Level Goal
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time

### Level 25 - 26
Level Goal
Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.

Commands you may need to solve this level
ssh, cat, more, vi, ls, id, pwd

### Level 26 - 27
Level Goal
Good job getting a shell! Now hurry and grab the password for bandit27!

Commands you may need to solve this level
ls

### Level 27 - 28
Level Goal
There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27.

Clone the repository and find the password for the next level.

Commands you may need to solve this level
git


### Level 28 - 29
Level Goal
There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28.

Clone the repository and find the password for the next level.

Commands you may need to solve this level
git


### Level 29 - 30
Level Goal
There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.

Clone the repository and find the password for the next level.

Commands you may need to solve this level
git

### Level 30 - 31
Level Goal
There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30.

Clone the repository and find the password for the next level.

Commands you may need to solve this level
git

### Level 31 - 32
Level Goal
There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31.

Clone the repository and find the password for the next level.

Commands you may need to solve this level
git

### Level 32 - 33
Level Goal
After all this git stuff, it’s time for another escape. Good luck!

Commands you may need to solve this level
sh, man

### Level 33 - 34
**At this moment, level 34 does not exist yet.**
