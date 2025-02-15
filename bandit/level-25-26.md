# [Level 25 to 26](https://overthewire.org/wargames/bandit/bandit26.html) - Breaking out of a restricted environment with more and vim

- Login
```
SSH: ssh bandit25@bandit.labs.overthewire.org -p 2220
Password: iCi86ttT4KSNe1armKiwbQNmB3YJP3q4

```
- Exercise: Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it. NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.
- Background:
  - Each user has a user default shell -> Can be found a the `/etc/passwd` file
- Solution:
  - Check what shell bandit26 uses
```bash
bandit25@bandit:~$ cat /etc/passwd | grep bandit26
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
bandit25@bandit:~$ ls -la /usr/bin/showtext
-rwxr-xr-x 1 root root 58 Sep 19 07:08 /usr/bin/showtext
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```
  - Use private key to connect
```bash
bandit25@bandit:~$ ssh bandit26@localhost -i bandit26.sshkey -p 2220
```
  - Make window smaller so that "more" appears
  - Use `v` to start up an editor at the current line
  - Change shell in vi
```bash
:set shell? shell=/usr/bin/showtext
:set shell=/bin/bash
:set shell? shell=/bin/bash
:shell
bandit26@bandit:~$ cat /etc/bandit_pass/bandit26
```
- Password: `s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ`
