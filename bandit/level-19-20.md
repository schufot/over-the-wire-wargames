# [Level 19 to 20](https://overthewire.org/wargames/bandit/bandit20.html) - Suid and linux permissions

- Login
```
SSH: ssh bandit19@bandit.labs.overthewire.org -p 2220
Password: cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
```
- Exercise: To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.
- Background:
  - `setuid` and `setgid` (short for set user identity and set group identity) allow users to run an executable with the file system permissions of the executable's owner or group respectively and to change behaviour in directories
- Solution:
  - ls -la: check who the owner of the of the setuid binary is (owner is bandit20 and the group is bandit19, user bandit19 can execute the binary, but the binary is executed as user bandit20)
```bash
bandit19@bandit:~$ ls -la
total 36
drwxr-xr-x  2 root     root      4096 Sep 19 07:08 .
drwxr-xr-x 70 root     root      4096 Sep 19 07:09 ..
-rwsr-x---  1 bandit20 bandit19 14880 Sep 19 07:08 bandit20-do
-rw-r--r--  1 root     root       220 Mar 31  2024 .bash_logout
-rw-r--r--  1 root     root      3771 Mar 31  2024 .bashrc
-rw-r--r--  1 root     root       807 Mar 31  2024 .profile
bandit19@bandit:~$ ./bandit20-do 
Run a command as another user.
  Example: ./bandit20-do id
bandit19@bandit:~$ ./bandit20-do ls /etc/bandit_pass
bandit0   bandit11  bandit14  bandit17  bandit2   bandit22  bandit25  bandit28  bandit30  bandit33  bandit6  bandit9
bandit1   bandit12  bandit15  bandit18  bandit20  bandit23  bandit26  bandit29  bandit31  bandit4   bandit7
bandit10  bandit13  bandit16  bandit19  bandit21  bandit24  bandit27  bandit3   bandit32  bandit5   bandit8
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```
- Password: `0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`
