# [Level 22 to 23](https://overthewire.org/wargames/bandit/bandit22.html) - Cronjobs

- Login
```
SSH: ssh bandit22@bandit.labs.overthewire.org -p 2220
Password: tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```
- Exercise: A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed. NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.
- Background:
  - cron: job scheduler, most suitable for scheduling repetitive tasks
  - crond - daemon to execute scheduled commands
  - crontab - tables for driving cron
- Solution:
```bash
bandit22@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
bandit22@bandit:/etc/cron.d$ /usr/bin/cronjob_bandit23.sh
Copying passwordfile /etc/bandit_pass/bandit22 to /tmp/8169b67bd894ddbb4412f91573b38db3
```
  - Substitute $myname with bandit23, execute it and the result is the filename
```bash
bandit22@bandit:/etc/cron.d$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:/etc/cron.d$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```
- Password: `0Zf11ioIjMVN551jX3CmStKLYqjk54Ga`
