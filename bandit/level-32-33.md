# [Level 32 to 33](https://overthewire.org/wargames/bandit/bandit33.html) - Linux variables and shell escape
- Login
```
SSH: ssh bandit32@bandit.labs.overthewire.org -p 2220
Password: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
```
- Exercise: After all this git stuff, it’s time for another escape. Good luck!
- Background:
  - Linux has Variables called local variables (valid in current shell), shell variables (set up by shell) and environment variables (valid systemwide)
  - These variables have their names in uppercase only. They are defined by writing `VAR_NAME=var_value` in the command line. To see the content of a variable, you can write `echo $VAR_NAME`
  - To print all environment variables, use `printenv`
    - `TERM` -  current terminal emulation
    - `HOME` - the path to home directory of currently logged in user
    - `LANG` - current locales settings
    - `PATH` - directory list to be searched when executing commands
    - `PWD` - pathname of the current working directory
    - `SHELL/0` - the path of the current user’s shell
    - `USER` - currently logged-in user
- Solution:
  - When using ssh to get access to the machine, we get: `WELCOME TO THE UPPERCASE SHELL`
```bash
WELCOME TO THE UPPERCASE SHELL
>> ls
sh: 1: LS: Permission denied
>> $0
$ ls -la
total 36
drwxr-xr-x  2 root     root      4096 Sep 19 07:08 .
drwxr-xr-x 70 root     root      4096 Sep 19 07:09 ..
-rw-r--r--  1 root     root       220 Mar 31  2024 .bash_logout
-rw-r--r--  1 root     root      3771 Mar 31  2024 .bashrc
-rw-r--r--  1 root     root       807 Mar 31  2024 .profile
-rwsr-x---  1 bandit33 bandit32 15136 Sep 19 07:08 uppershell
$ cat /etc/bandit_pass/bandit33
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
```
- Password: `tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0`
