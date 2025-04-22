Bandit Wargame Writeup
A level-by-level walkthrough of the Bandit wargame from OverTheWire.
Level 0 ➜ Level 1
Goal: SSH into the remote machine using the provided credentials.

Username: bandit0Password: bandit0Port: 2220

Command Used:
ssh bandit0@bandit.labs.overthewire.org -p 2220

What Happened: Logged into the Bandit server using SSH. The custom port -p 2220 is used instead of default 22.

Real World Parallel: Like accessing a private server with non-standard SSH port (used in security setups or CTFs).

Level 1 ➜ Level 2
Goal: Read a file named - located in the home directory.

Command Used:
cat ./-

Why This Works:Normally, cat - tries to read from stdin. But using ./- tells the shell that - is a filename in the current directory.
Real World Parallel: In penetration testing or sysadmin work, filenames can be created to confuse tools or break scripts.

Level 2 ➜ Level 3
Goal: Find the password stored in a file with spaces in its name.

Command Used:
cat "spaces in this filename"

Why This Works: Wrapping the filename in quotes prevents the shell from treating the spaces as separate arguments.
Real World Parallel: Attackers or sysadmins may create confusing filenames to obfuscate files.
