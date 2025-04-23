OverTheWire: Bandit, Level 0-3 Write-up
======================================

Table of Contents
-----------------
- [Bandit Level 00](#bandit-level-00)
- [Bandit Level 01](#bandit-level-01)
- [Bandit Level 02](#bandit-level-02)
- [Bandit Level 03](#bandit-level-03)

Bandit Level 00
----------------

### Problem Description:
Level 0 is a welcome gift to get you started with the real difficulties.

# Solution & Explanation:
To begin, you must understand how to use the secure shell (SSH) protocol to connect to the bandit.labs.overthewire.org server. If you're using Linux, you may access the server by running the following command:


sasha@SecurityBox:~$ ssh bandit.labs.overthewire.org -l bandit0 -p 2220


If you're using Windows, though, you won't find an SSH client by default. While there are several great SSH clients available for use in Windows environments, I recommend PuTTY since it is straightforward and relatively compact.

Once connected, you will access the bandit0 shell.

---

Bandit Level 01
---------------

Problem Description:
At this level, you are tasked with finding a file named `readme` in the current directory. The password for the next level is hidden inside this file.

Solution & Explanation:
This level is quite simple. The task is to read the contents of a file named `readme`. To do this, we can use the `cat` command to display the content of the file.

- Run the following command to list the files in the directory:

bandit0@bandit:~$ ls readme


- Now, use `cat` to read the content of the file:

bandit0@bandit:~$ cat readme boJ9jbbUNNfktd78OOpsqOltutMc3MY1


The password for the next level (Level 2) is:

boJ9jbbUNNfktd78OOpsqOltutMc3MY1


---

Bandit Level 02
---------------

Problem Description:
For Level 2, you will encounter a file named `-` (a dash). The goal is to figure out how to read the file without causing errors due to the special character.

Solution & Explanation:
If you try to use `cat -` directly, the terminal will interpret the `-` as an option for `cat` rather than as a file name. To resolve this, you can provide the file path using either the `./` or the absolute path.

- First, list the files in the directory to confirm that the file exists:

bandit1@bandit:~$ ls

- Use `cat` with `./` to specify the file:

bandit1@bandit:~$ cat ./- CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9


The password for the next level (Level 3) is:

CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9


---

Bandit Level 03
---------------

Problem Description:
In this level, you need to access a file with spaces in its name. The goal is to figure out how to properly read the file using the `cat` command.

Solution & Explanation:
When dealing with file names that contain spaces, you need to either escape the spaces with a backslash `\` or enclose the entire file name in quotes.

- First, list the files in the directory to confirm the name of the file:

bandit2@bandit:~$ ls spaces in this filename


- To read the file using `cat`, you can either:
- Escape the spaces with a backslash:
bandit2@bandit:~$ cat spaces\ in\ this\ filename

- Or, use quotes around the entire file name:
bandit2@bandit:~$ cat “spaces in this filename”


The password for the next level (Level 4) is:

UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
