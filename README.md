---
description: >-
  If confuse how the given commands are work, use whatis <command> or man
  <command> for description.
---

# OverTheWire (Bandit)

## _**Level 0**_

![](<.gitbook/assets/image (5) (1) (1).png>)

Based on [https://www.wikihow.com/Use-SSH](https://www.wikihow.com/Use-SSH), the command is:

`ssh bandit0@bandit.labs.overthewire.org -p 2220`

And the password is `bandit0`. When successful, it will display:

![](<.gitbook/assets/image (1) (1) (1).png>)

## _**Level 0 → Level 1**_

The password for the next level is stored in a file called **readme** located in the home directory.

Use `ls` command to list the files, and `cat` command to read the data in file which is password for Level 1.

![](<.gitbook/assets/image (2) (1) (1).png>)

## _**Level 1 → Level 2**_

The password for the next level is stored in a file called **-** located in the home directory.

Use `ls` command to list the files.

Use `./-` command to open **"dashed filename ( - )"** which is `cat ./-` _****_ to get the password for Level 2.

![](<.gitbook/assets/image (3) (1).png>)

## _**Level 2 → Level 3**_

The password for the next level is stored in a file called **spaces in this filename** located in the home directory.

Use `ls` command to list the files.

Use `'spaces in this filename'` command to open **"dashed filename ( - )"** which is `cat 'spaces in this filename'` _****_ to get the password for Level 3.

![](<.gitbook/assets/image (4) (1).png>)

## _**Level 3 → Level 4**_

The password for the next level is stored in a hidden file in the **inhere** directory.

Use `ls` command to list the files , `-a` option to list ALL the files in **inhere** directory

`ls -a inhere` and it shows `.hidden` filename.

Use `cd inhere/` to change directory into **inhere** and **** `cat .hidden` **** to read the hidden file to get the password for Level 4.

![](<.gitbook/assets/image (1) (1) (1) (1).png>)

## _**Level 4 → Level 5**_

The password for the next level is stored in the only human-readable file in the **inhere** directory.

Use `ls -R` command to list all the files in **inhere**.

Use `file ./inhere/*` to display file type of all the files in the **inhere** directory. ASCII text is human-readable file.

Use `cat ./inhere/-file07` to get the password for Level 5.

![](<.gitbook/assets/image (1) (1).png>)

## _**Level 5 → Level 6**_

The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

* human-readable
* 1033 bytes in size
* not executable

Use `find ./inhere/* -size 1033c ! -executable` which is:

`find` command to search for files and directories,

`./inhere/*` command to display file type of all the files in the **inhere** directory,

`-size 1033c` option to find the files with size 1033 bytes, in Linux '`c`' represents to byte,

and `! -executable` option to find non executable files, in Linux '`!`' is similar to '`-not`'.

Use `cat ./inhere/maybehere07/.file2` to get the password for Level 6.

![](<.gitbook/assets/image (9) (1).png>)

## _**Level 6 → Level 7**_

The password for the next level is stored **somewhere on the server** and has all of the following properties:

* owned by user bandit7
* owned by group bandit6
* 33 bytes in size

_Use ****_ `find / -user bandit7 -group bandit6 -size 33c` which is:

`find /` command which is to find in the whole server,

`-user bandit7` option which is owned by user bandit7,

`-group bandit6` option which is owned by group bandit6,

and `-size 33c` option which is the size of file is 33 bytes. All the permission is denied but 1 file display the directory: `/var/lib/dpkg/info/bandit7.password`

![](<.gitbook/assets/image (15) (1).png>)

Use `cat /var/lib/dpkg/info/bandit7.password` to get the password for Level 7.

![](<.gitbook/assets/image (5) (1).png>)

## _**Level 7 → Level 8**_

The password for the next level is stored in the file **data.txt** next to the word **millionth.**

Use `grep` command to print lines that match with the given word which is **millionth**, and put text file that the password is stored.

![](<.gitbook/assets/image (6) (1).png>)

The password for Level 8 is inline with **millionth**, but remember, the password is not include with that word.

## _**Level 8 → Level 9**_

The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once.

Use `sort` command to sorting text files, following with the file, and `uniq` command to omit repeated lines.

`-c` option is to count the number of occurrences and `-u` option is to print unique lines.

![](<.gitbook/assets/image (16) (1) (1).png>)

Number 1 represents the count of occurrences and next to it is the password for Level 9.

## _**Level 9 → Level 10**_

The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.

_Use_ `cat data.txt | strings | grep =` which is `cat` command for get the data following by the text file, `strings` command to print the strings of printable characters and `grep` command to print lines matched. It shows the password of Level 10.

![](<.gitbook/assets/image (19) (1) (1).png>)

## _**Level 10 → Level 11**_

The password for the next level is stored in the file **data.txt**, which contains base64 encoded data_**.**_

_`cat data.txt` command is to get the data from **data.txt** and `base64` command to encode or decode data and print to standard output._&#x20;

_`-d` option is to decode the following data. After decode the data, it will print the password for Level 11._

![](<.gitbook/assets/image (10) (1) (1).png>)

## _**Level 11 → Level 12**_

The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions_**.**_

Based on Wikipedia, to apply ROT13 to a piece of text, just examine its alphabetic letters and replace each one with the letter 13 places further along in the alphabet, wrapping back to the beginning if required.

![](<.gitbook/assets/image (2) (1).png>)

So, to read the data from **data.txt**, use `cat data.txt` command with `tr 'A-Za-z' 'N-ZA-Mn-za-m'`. It will show the password for Level 12.

![](<.gitbook/assets/image (3).png>)

## _**Level 12 → Level 13**_

The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir_**.**_

Before make the file become hexdump, first, we need to create a new directory using `mkdir /tmp/hafizi` command.

Then, copy **data.txt** to the new directory using `cp data.txt /tmp/hafizi` command.

Because of the file is hexdump, so we should revert the file using `xxd -r data.txt data command`.

After revert it, use `file` command to determine file type. Then decompress it based on type of file.

![](<.gitbook/assets/image (7) (1).png>)

When the type of file is tar archive, change the file to `.tar` and extract it using `tar xf` command.&#x20;

![](<.gitbook/assets/image (4).png>)

Then, it will appear another file. Extract the another file and if it messed, remove the old file with `rm` command following with the name file.

![](<.gitbook/assets/image (12).png>)

Lastly, the type of file is show ASCII text which means the file is done. Use cat command to get the password for Level 13.

![](<.gitbook/assets/image (18) (1).png>)

## _**Level 13 → Level 14**_

The password for the next level is stored in **/etc/bandit\_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. _****_** Note:** **localhost** is a hostname that refers to the machine you are working on.

Use `ssh` command to open SSH client, and because of the SSH key is private, use `-i` option to read the private file. And because of the user is bandit14, so the localhost is bandit14. Type 'yes' to continue.

![](<.gitbook/assets/image (11) (1) (1).png>)

Use `cat /etc/bandit_pass/bandit14` command to get the password for Level 14.

![](<.gitbook/assets/image (8) (1).png>)

## _**Level 14 → Level 15**_

The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.

Use the current password which is stored in `/etc/bandit_pass/bandit14` directory.

Use telnet command and the number of port to connecting to localhost, and use the password.&#x20;

If correct, it will show the password for Level 15.

![](<.gitbook/assets/image (14) (1).png>)

## _**Level 15 → Level 16**_

The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL encryption.

**Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign\_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…**

First, we need to get the current password which is stored in _****_ `/etc/bandit_pass/bandit15` directory.

To use SSL encyrption, use `openssl s_client` command with `localhost:30001`.

If correct, it will show the password for Level 16.

![](<.gitbook/assets/image (13).png>)

## _**Level 16 → Level 17**_

The credentials for the next level can be retrieved by submitting the password of the current level to **a port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

First, we need to get the current password which is stored in _****_ `/etc/bandit_pass/bandit16` directory.

![](<.gitbook/assets/image (19) (1).png>)

Use `nmap` command to find out the suitable ports that listening on them which in the range 31000 to 32000. Nmap is network exploration tool and port scanner which is the right tools in this task.

![](<.gitbook/assets/image (11) (1).png>)

There are 2 results; 31518 and 31790. To find out, use `openssl s_client` command and enter the current password. The right server will give the private key and another one will send back the password. Copy the whole private key to login to Level 17.

![](<.gitbook/assets/image (16) (1).png>)

Find the password for Level 17 that stored in`/etc/bandit_pass/bandit1`_**7**_ `` directory.

![](<.gitbook/assets/image (17) (1).png>)

## _**Level 17 → Level 18**_

There are 2 files in the homedirectory: **passwords.old and passwords.new**. The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old and passwords.new.**

Use diff command to differentiate  between two files.

Use the second password because already told that the password for Level 18 is in **password.new**.

![](<.gitbook/assets/image (10) (1).png>)

## _**Level 18 → Level 19**_

The password for the next level is stored in a file **readme** in the homedirectory. Unfortunately, someone has modified **.bashrc** to log you out when you log in with SSH.

![](<.gitbook/assets/image (7).png>)

This is occur when we are trying to login normally. Try to bypass to see the files by:

`ssh bandit18@bandit.labs.overthewire.org -p 2220 ls`

![](<.gitbook/assets/image (6).png>)

And it successful. Then, try to read **readme** file by:

`ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme`

It shows the password for Level 19 successfully.

![](<.gitbook/assets/image (19).png>)

## _**Level 19 → Level 20**_

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit\_pass), after you have used the setuid binary.

The password for Level 20 that stored in`/etc/bandit_pass/bandit20` directory, but permission is denied because the files only allow for user bandit 20.

![](<.gitbook/assets/image (11).png>)

To read the password, use the binary file as user bandit20.

![](<.gitbook/assets/image (15).png>)

## _**Level 20 → Level 21**_

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

**NOTE:** Try connecting to your own network daemon to see if it works as you think_**.**_

Use the directory of password for Level 20 to compare with another terminal, use `nc` command as netcap, `-l` option to be listen mode, the hostname and the port.

The port in both terminal must same, for example `-p 3636`.

![](<.gitbook/assets/image (5).png>)

## _**Level 21 → Level 22**_

A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

Use `cd` command to change directory to `/etc/cron.d`. Use `ls` command to list the files.

![](<.gitbook/assets/image (20).png>)

We are looking password for Level 22, so choose the file `cronjob_bandit22`. Use `cat` command to read the file.

![](<.gitbook/assets/image (1).png>)

The, try to read the file in `/usr/bin/cronjob_bandit22.sh`.

![](<.gitbook/assets/image (16).png>)

That is not the password since it is a file. So read the file in `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv` to get the password for Level 22.

![](<.gitbook/assets/image (8).png>)

## _**Level 22 → Level 23**_

A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

**NOTE:** Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

Use `cd` command to change directory to `/etc/cron.d`. Use `ls -al` command to list the files. _****_ We are looking password for Level 23, so choose the file `cronjob_bandit23`. Use `cat` command to read the file. The, try to read the file in `/usr/bin/cronjob_bandit23.sh`.

![](<.gitbook/assets/image (14).png>)

Just like previous level, if just read the file, the permission is denied.

![](<.gitbook/assets/image (9).png>)

From it, we know that `$mytarget` is not the right answer. Based on it `myname = $(whoami)`.

As we know, the file contains the password for Level 23. So, `myname = (whoami) = bandit23`.

From the equation, replace `$myname` to `bandit23`.

![](<.gitbook/assets/image (18).png>)

So, `mytarget = $8ca319486bfbbc3663ea0fbe81326349`. Then, read and replace `/tmp/$mytarget` to `/tmp/8ca319486bfbbc3663ea0fbe81326349` to get the password for Level 23.

![](<.gitbook/assets/image (10).png>)

## _**Level 23 → Level 24**_

A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

**NOTE:** This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

**NOTE 2:** Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

Use `cd` command to change directory to `/etc/cron.d`. Use `ls -al` command to list the files. _****_ We are looking password for Level 2_**4**_, so choose the file `cronjob_bandit24`. Use `cat` command to read the file. The, try to read the file in `/usr/bin/cronjob_bandit24.sh`.Use `cd` command to change directory to `/etc/cron.d`. Use `ls -al` command to list the files. _****_ We are looking password for Level 23, so choose the file `cronjob_bandit24`. Use `cat` command to read the file. The, try to read the file in `/usr/bin/cronjob_bandit24.sh`.

![](<.gitbook/assets/image (21).png>)

Based on it `myname = $(whoami)`. So, `myname = (whoami) = bandit24`. As we know, `/var/spool/bandit24` contains the password for Level 24, but the permission is denied to open it and it will be deleted. So, create a directory: `mkdir /tmp/bandit24`. Then change the directory: `cd /tmp/bandit24`. Create the file name `bandit24.sh` using `vim` command and edit it:

`#!/bin/bash`&#x20;

`cat /etc/bandit_pass/bandit24 > /tmp/bandit24/password`

Change file mode of `bandit24.sh` and `password` to 777 and change the file timestamps of password:

`chmod 777 bandit24.sh`

`touch password`

`chmod 777 password`

Read the password file and it will display the password for Level 24.

![](<.gitbook/assets/image (17).png>)

## _**Level 24 → Level 25**_

A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

