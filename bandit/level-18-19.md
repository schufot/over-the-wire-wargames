# [Level 18 to 19](https://overthewire.org/wargames/bandit/bandit19.html) - Advanced SSH, remote command execution

- Login
```
SSH: ssh bandit18@bandit.labs.overthewire.org -p 2220
Password: x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```
- Exercise: The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.
- Background:
  - `.bashrc`: runs every time a terminal is loaded -> also runs when logging in through SSH
- Solution:
  - ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
- Password: `cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8`
