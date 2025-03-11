# OverTheWire-Walkthrough

## Introduction

Here's a quick write-up of the OverTheWire bandit wargame (https://overthewire.org/wargames/bandit/). All levels will be included. For those that don't want to be spoiled, I will give few hints before digging deep into the level.
Also, don't forget to create a password file containing all the passwords you fought. It's a hassle to go back at level 0 when you were level 10 because your PC shut down for example.


### Level 0
Level Goal :
*The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.*
![bandit0](https://github.com/user-attachments/assets/6375267d-5cbd-47b7-87a9-ac3aa5666f6a)

So first of all, we will be using SSH in order to connect to the host on port 2220. Here's the command line :
IMAGE BANDIT0

In order to connect to a SSH we use this topology : username@IP_ADRESS or username@DOMAIN_NAME. Since they gave us the username, domain name and also the password, we can confidently write it like this : bandit0@bandit.labs.overthewire.org . If you don't specify the port, it will automatically try to connect to the port 22 and it will give us an error. This is why -p 2220 is important. Lastly, don't forget to invoke sudo.

If it worked, you should see this. Simply type the password they gave us : 
IMAGE BANDIT0_1

This will lead us to be on the bandit0 machine, which should be like this :
IMAGE BANDIT0_2


### Level 0 - 1
Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

Commands you may need to solve this level
ls , cd , cat , file , du , find

We have now access to the bandit0 machine, let's **ls** in order to discover what is in there. **ls** can let us see the content of a directory.
IMAGE bandit0_3
Bingo ! Now we just have to open this file using **cat**  . **cat** let us print the file in a standard output.
IMAGE BANDIT0_4

Bravo ! This one was fast and easy but still ! You completed your first bandit level ! Don't forget to **save** the **password** in your password file also.

*Note : You wouldn't be able to hop from level to level using SSH from another SSH session. You need to connect to a level using your own root machine and not the bandit one !!*

### Level 1 - 2

Level Goal :
*The password for the next level is stored in a file called - located in the home directory*

Commands you may need to solve this level :
**ls , cd , cat , file , du , find**

Helpful Reading Material
*Google Search for “dashed filename”*
*Advanced Bash-scripting Guide - Chapter 3 - Special Characters*

Ok, so first of all, if you have trouble login in to this level, don't forget that the SSH username is now bandit1 for the level 1-2, and bandit2 for the level 2-3, and so on..

Now, we need to  find and open the "-" directory. So we find the "-" directory by using **ls**, then we use **cat** again but we have a problem when we do that :
IMAGE BANDIT1

Indeed, bash doesn't understand that we want to see the file since it is called like that. A little trick that we can do is to put "./" before the directory name so it can get understand by BASH just like that :
IMAGE BANDIT1_1

Yessir ! Let's move on !

### Level 2 - 3
Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory

Commands you may need to solve this level
ls , cd , cat , file , du , find

In this level, we need to find a file and open it. Let's do that.
I will **ls** then open the file using **cat** but as soon as I do it, it gave me this :
IMAGE BANDIT2

Ok so this is why you don't name a file that has spaces without using underscore or some other stuff. Got it. Let's find how to open it.

In this article (https://linuxhandbook.com/filename-spaces-linux/) we can see that by wrapping the whole name, you can open it (Example : cat "spaces in this filename") . Let's see if it work :
IMAGE BANDIT2_1

Great ! That was easier than I thought ! There was also another way to open it, using backslashes (Example : cat spaces\ in\ this\ filename) but I find it harder to type. Still good to know.



### Level 3 - 4

Level Goal
The password for the next level is stored in a hidden file in the inhere directory.

Commands you may need to solve this level
ls , cd , cat , file , du , find

An hidden file ? I have the perfect command for that : **ls -la** .
IMAGE BANDIT3

the -a argument in ls show us the hidden file in a directory. It is useful and should be learned by everyone. Anyway, let's **cat** this file :

Yes sir ! Let's see what's next.


### Level 4 - 5
Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

Commands you may need to solve this level
ls , cd , cat , file , du , find

Alright. So in this level I have to find the only human-readable file in the directory. I wanted to know, first, if you could manually **cat** every file, which you can do. I find the password like that ! :
IMAGE BANDIT4

However, I do not think it was intended to be the primary source of finding, so I made some research in order to know how to do it using the command **find** . After few minutes, I came to something : ```find /path/to/search -type f -exec file {} + | grep ": text"```
In this one, find . means it search from the directory we are, -type f means that it searchs for files. -exec file {} + open every file during the search. grep text is a command that search for specific name (here, only text so human readable file).
Let's try it :
IMAGE BANDIT4_1

Indeed it worked ! 



### Level 5 - 6
### Level 6 - 7
### Level 7 - 8
### Level 8 - 9
### Level 9 - 10
### Level 10 - 11
### Level 11 - 12
### Level 12 - 13
### Level 13 - 14
### Level 14 - 15
### Level 15 - 16
### Level 16 - 17
### Level 17 - 18
### Level 18 - 19
### Level 19 - 20
### Level 20 - 21
### Level 21 - 22
### Level 22 - 23
### Level 23 - 24
### Level 24 - 25
### Level 25 - 26
### Level 26 - 27
### Level 27 - 28
### Level 28 - 29
### Level 29 - 30
### Level 30 - 31
### Level 31 - 32
### Level 32 - 33
### Level 33 - 34

