# [Level 17 to 18](https://overthewire.org/wargames/bandit/bandit18.html) - Find differences in a file

- Login
```
SSH: ssh -i sshkey.private bandit17@bandit.labs.overthewire.org -p 2220
Password: / (Private key from previous level)
```
- Exercise: There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new. NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19
- Background:
  - cat - concatenate files and print on the standard output
  - grep - print lines that match patterns
  - ls - list directory contents
  - diff - compare files line by line
- Solution:
  - diff passwords.old passwords.new
- Password: `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`

