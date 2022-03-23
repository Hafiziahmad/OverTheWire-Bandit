---
description: >-
  If confuse how the given commands are work, use whatis <command> or man
  <command> for description.
---

# OverTheWire (Bandit)

## _**Level 0**_

![](<.gitbook/assets/image (5) (1).png>)

Based on [https://www.wikihow.com/Use-SSH](https://www.wikihow.com/Use-SSH), the command is:

`ssh bandit0@bandit.labs.overthewire.org -p 2220`

And the password is `bandit0`. When successful, it will display:

![](<.gitbook/assets/image (1) (1).png>)

## _**Level 0 → Level 1**_

The password for the next level is stored in a file called **readme** located in the home directory.

Use `ls` command to list the files, and `cat` command to read the data in file which is password for Level 1.

![](<.gitbook/assets/image (2) (1).png>)

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

![](<.gitbook/assets/image (1) (1) (1).png>)

## _**Level 4 → Level 5**_

The password for the next level is stored in the only human-readable file in the **inhere** directory.

Use `ls -R` command to list all the files in **inhere**.

Use `file ./inhere/*` to display file type of all the files in the **inhere** directory. ASCII text is human-readable file.

Use `cat ./inhere/-file07` to get the password for Level 5.

![](<.gitbook/assets/image (1).png>)

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

![](<.gitbook/assets/image (9).png>)

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

![](<.gitbook/assets/image (15).png>)

Use `cat /var/lib/dpkg/info/bandit7.password` to get the password for Level 7.

![](<.gitbook/assets/image (5).png>)

## _**Level 7 → Level 8**_

The password for the next level is stored in the file **data.txt** next to the word **millionth.**

Use `grep` command to print lines that match with the given word which is **millionth**, and put text file that the password is stored.

![](<.gitbook/assets/image (6).png>)

The password for Level 8 is inline with **millionth**, but remember, the password is not include with that word.

## _**Level 8 → Level 9**_

The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once.

Use `sort` command to sorting text files, following with the file, and `uniq` command to omit repeated lines.

`-c` option is to count the number of occurrences and `-u` option is to print unique lines.

![](<.gitbook/assets/image (16).png>)

Number 1 represents the count of occurrences and next to it is the password for Level 9.

## _**Level 9 → Level 10**_

The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.

_Use_ `cat data.txt | strings | grep =` which is `cat` command for get the data following by the text file, `strings` command to print the strings of printable characters and `grep` command to print lines matched. It shows the password of Level 10.

![](<.gitbook/assets/image (19).png>)

## _**Level 10 → Level 11**_

The password for the next level is stored in the file **data.txt**, which contains base64 encoded data_**.**_

_`cat data.txt` command is to get the data from **data.txt** and `base64` command to encode or decode data and print to standard output._&#x20;

_`-d` option is to decode the following data. After decode the data, it will print the password for Level 11._

![](<.gitbook/assets/image (10).png>)

## _**Level 11 → Level 12**_

The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions_**.**_

Based on Wikipedia, to apply ROT13 to a piece of text, just examine its alphabetic letters and replace each one with the letter 13 places further along in the alphabet, wrapping back to the beginning if required.

![](<.gitbook/assets/image (2).png>)

So, to read the data from **data.txt**, use `cat data.txt` command with `tr 'A-Za-z' 'N-ZA-Mn-za-m'`. It will show the password for Level 12.

![](<.gitbook/assets/image (3).png>)

## _**Level 12 → Level 13**_

The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir_**.**_

Before make the file become hexdump, first, we need to create a new directory using `mkdir /tmp/hafizi` command.

Then, copy **data.txt** to the new directory using `cp data.txt /tmp/hafizi` command.

Because of the file is hexdump, so we should revert the file using `xxd -r data.txt data command`.

After revert it, use `file` command to determine file type. Then decompress it based on type of file.

![](<.gitbook/assets/image (7).png>)

When the type of file is tar archive, change the file to `.tar` and extract it using `tar xf` command.&#x20;

![](<.gitbook/assets/image (4).png>)

Then, it will appear another file. Extract the another file and if it messed, remove the old file with `rm` command following with the name file.

![](<.gitbook/assets/image (12).png>)

Lastly, the type of file is show ASCII text which means the file is done. Use cat command to get the password for Level 13.

![](<.gitbook/assets/image (18).png>)

## _**Level 13 → Level 14**_

The password for the next level is stored in **/etc/bandit\_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. _****_** Note:** **localhost** is a hostname that refers to the machine you are working on.

Use `ssh` command to open SSH client, and because of the SSH key is private, use `-i` option to read the private file. And because of the user is bandit14, so the localhost is bandit14. Type 'yes' to continue.

![](<.gitbook/assets/image (11).png>)

Use `cat /etc/bandit_pass/bandit14` command to get the password for Level 14.

![](<.gitbook/assets/image (8).png>)

## _**Level 14 → Level 15**_

The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.

Use the current password which is stored in `/etc/bandit_pass/bandit14` directory.

Use telnet command and the number of port to connecting to localhost, and use the password.&#x20;

If correct, it will show the password for Level 15.

![](<.gitbook/assets/image (14).png>)

## _**Level 15 → Level 16**_

The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL encryption.

**Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign\_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…**

First, we need to get the current password which is stored in _****_ `/etc/bandit_pass/bandit15` directory.

To use SSL encyrption, use `openssl s_client` command with `localhost:30001`.

If correct, it will show the password for Level 16.

![](<.gitbook/assets/image (13).png>)

## _**Level 16 → Level 17**_

The credentials for the next level can be retrieved by submitting the password of the current level to **a port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

