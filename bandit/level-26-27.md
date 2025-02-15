# [Level 26 to 27](https://overthewire.org/wargames/bandit/bandit27.html) - Breaking out of a restricted environment with more and vim and SUID Binary

- Login
```
SSH: ssh bandit26@bandit.labs.overthewire.org -p 2220
Password: s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ

```
- Exercise: Good job getting a shell! Now hurry and grab the password for bandit27!
- Background:
- Solution:
```bash
bandit26@bandit:~$ ls
bandit27-do  text.txt
bandit26@bandit:~$ file bandit27-do
bandit27-do: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=368cd8ac4633fabdf3f4fb1c47a250634d6a8347, for GNU/Linux 3.2.0, not stripped
bandit26@bandit:~$ ./bandit27-do
Run a command as another user.
  Example: ./bandit27-do id
bandit26@bandit:~$ ./bandit27-do whoami
bandit27
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
```
- Password: `upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB`
