```markdown
OverTheWire: Bandit Levels 0–6 Write-Up

Table of Contents
- [Bandit Level 00](#bandit-level-00)
- [Bandit Level 01](#bandit-level-01)
- [Bandit Level 02](#bandit-level-02)
- [Bandit Level 03](#bandit-level-03)+q
- [Bandit Level 04](#bandit-level-04)
- [Bandit Level 05](#bandit-level-05)
- [Bandit Level 06](#bandit-level-06)

---

Bandit Level 00

Problem Description:
Level 0 is a welcome gift to get you started with the real difficulties.

Solution & Explanation:
To begin, you must understand how to use the secure shell (SSH) protocol to connect to the bandit.labs.overthewire.org server. If you're using Linux, you may access the server by running the following command:

```bash
sasha@SecurityBox:~$ ssh bandit.labs.overthewire.org -l bandit0 -p 2220

```

If you're using Windows, though, you won't find an SSH client by default. While there are several great SSH clients available for use in Windows environments, I recommend PuTTY since it is straightforward and relatively compact.

Once connected, you will access the `bandit0` shell.

----------

## Bandit Level 01

### Problem Description:

At this level, you are tasked with finding a file named `readme` in the current directory. The password for the next level is hidden inside this file.

### Solution & Explanation:

This level is quite simple. The task is to read the contents of a file named `readme`. To do this, we can use the `cat` command to display the content of the file.

Run the following command to list the files in the directory:

```bash
bandit0@bandit:~$ ls readme

```

Now, use `cat` to read the content of the file:

```bash
bandit0@bandit:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1

```

The password for the next level (Level 2) is:

```
boJ9jbbUNNfktd78OOpsqOltutMc3MY1

```

----------

## Bandit Level 02

### Problem Description:

For Level 2, you will encounter a file named `-` (a dash). The goal is to figure out how to read the file without causing errors due to the special character.

### Solution & Explanation:

If you try to use `cat -` directly, the terminal will interpret the `-` as an option for `cat` rather than as a file name. To resolve this, you can provide the file path using either the `./` or the absolute path.

First, list the files in the directory to confirm that the file exists:

```bash
bandit1@bandit:~$ ls

```

Use `cat` with `./` to specify the file:

```bash
bandit1@bandit:~$ cat ./-

```

The password for the next level (Level 3) is:

```
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

```

----------

##  Bandit Level 03

### Problem Description:

In this level, you need to access a file with spaces in its name. The goal is to figure out how to properly read the file using the `cat` command.

### Solution & Explanation:

When dealing with file names that contain spaces, you need to either escape the spaces with a backslash `\` or enclose the entire file name in quotes.

First, list the files in the directory to confirm the name of the file:

```bash
bandit2@bandit:~$ ls "spaces in this filename"

```

To read the file using `cat`, you can either:

-   Escape the spaces with a backslash:
    

```bash
bandit2@bandit:~$ cat spaces\ in\ this\ filename

```

-   Or, use quotes around the entire file name:
    

```bash
bandit2@bandit:~$ cat "spaces in this filename"

```

The password for the next level (Level 4) is:

```
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

```

----------

## Bandit Level 04

### Problem Description:

In this level, you have several files, but only one contains the password for the next level. You need to find the file that contains the password.

### Solution & Explanation:

Because just one file is human-readable and contains the password for the following round, rather than accessing each file one by one and reading its content, we can print all of each text and spot the password using:

```bash
bandit4@bandit:~/inhere$ cat ./-file0*

```

The asterisk (`*`) is a wildcard that represents any number of unknown characters. This is useful when searching for documents or files but only remembering part of its name. Here’s what we got from using the command above:

```
�/`2ғ�%��rL~5�g��� �������p,k�;��r*��	�.!��C��J	�dx,�e�)�#��5��
                                                                       ��p��V�_���ׯ�mm������h!TQO�`�4"aל�߂phT��,�?��r�l$�?h�9('���!y�e�#�x�O��=��ly���~��A�f����-E�{���m�����ܗkoReBOKuIDDepwhWk7jZC0RTdopnAYKh

```

However, if you want to know which file contains the password, you can use the following:

```bash
bandit4@bandit:~/inhere$ find . -type f | xargs file

```

This command will show you which file is human-readable and contains the password:

```bash
bandit4@bandit:~/inhere$ find . -type f | xargs file
./-file07: ASCII text

```

Now, you can view the password:

```bash
bandit4@bandit:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh

```

The password for the next level (Level 5) is:

```
koReBOKuIDDepwhWk7jZC0RTdopnAYKh

```

----------

##  Bandit Level 05

### Problem Description:

You are now faced with many directories and need to find a file of a specific size that contains the password.

### Solution & Explanation:

We begin by listing the files in the current directory:

```bash
bandit5@bandit:~/inhere$ ls

```

The output will display many directories. We need to search for a specific file based on its size.

Use the `find` command to search for files of size 1033 bytes:

```bash
bandit5@bandit:~/inhere$ find . -type f -size 1033c

```

The output will show the path to the file containing the password:

```bash
./maybehere07/.file2

```

Now, read the file to get the password:

```bash
bandit5@bandit:~/inhere$ cat maybehere07/.file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7

```

The password for the next level (Level 6) is:

```
DXjZPULLxYr17uwoI01bNLQbtFemEgo7

```

----------

## Bandit Level 06

### Problem Description:

You are tasked with searching the entire filesystem for a file owned by the next user (`bandit7`), and the file will contain the password for the next level.

### Solution & Explanation:

This level is quite similar to the previous one. However, we need to search the entire system for a file owned by `bandit7` and belonging to `bandit6`.

Run the following command to search for the file:

```bash
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -type f -size 33c

```

The output will show the path to the file:

```bash
/var/lib/dpkg/info/bandit7.password

```

Now, read the file to get the password:

```bash
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

```

The password for the next level (Level 7) is:

```
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

```

----------
