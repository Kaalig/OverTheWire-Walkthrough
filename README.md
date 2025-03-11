# OverTheWire-Walkthrough

## Introduction

Here's a quick write-up of the OverTheWire bandit wargame (https://overthewire.org/wargames/bandit/). All levels will be included. For those that don't want to be spoiled, I will give few hints before digging deep into the level.
Also, don't forget to create a password file containing all the passwords you fought. It's a hassle to go back at level 0 when you were level 10 because your PC shut down for example.


### Level 0
Level Goal :
*The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.*

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
### Level 3 - 4
### Level 4 - 5
### Level 3 - 6
### Level 3 - 7
### Level 3 - 8
### Level 3 - 9
### Level 3 - 10
### Level 3 - 11
### Level 3 - 12
### Level 3 - 13
### Level 3 - 14
### Level 3 - 15
### Level 3 - 16
### Level 3 - 17
### Level 3 - 18
### Level 3 - 19
### Level 3 - 20
### Level 3 - 21
### Level 3 - 22
### Level 3 - 23
### Level 3 - 24
### Level 3 - 25
### Level 3 - 26
### Level 3 - 27
### Level 3 - 28
### Level 3 - 29
### Level 3 - 30
### Level 3 - 31
### Level 3 - 32
### Level 3 - 33
### Level 3 - 34

