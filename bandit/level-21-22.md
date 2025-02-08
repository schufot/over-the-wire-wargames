# [Level 21 to 22](https://overthewire.org/wargames/bandit/bandit22.html) - Setuid binary, netcat and background processes/jobs

- Login
```
SSH: ssh bandit21@bandit.labs.overthewire.org -p 2220
Password: EeoULMCra2q0dSkYj561DX7s1CpBuOBt
```
- Exercise: A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.
- Background:
  - cron: job scheduler, most suitable for scheduling repetitive tasks
  - crond - daemon to execute scheduled commands
  - crontab - tables for driving cron
- Solution:
```bash
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22 
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```
  - Cronjob runs the `/usr/bin/cronjob_bandit22.sh` file as bandit22 user -> Take a look at the bash file to know exactly what is being executed
```bash
bandit21@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
  - Creates a file in the `tmp` folder and gives read permission to everyone, then it copies the input of the bandit22 password file into the newly created file
```bash
bandit21@bandit:/etc/cron.d$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```
- Password: `tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q`
