# [Level 01 to 02](https://overthewire.org/wargames/bandit/bandit2.html) - Unusually named files

- Login
```
SSH: ssh bandit1@bandit.labs.overthewire.org -p 2220
Password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```
- Exercise: The password for the next level is stored in a file called - located in the home directory
- Background:
  - ls - list directory contents
  - cd - change the working directory
  - cat - concatenate files and print on the standard output
  - file - determine file type
  - du - estimate file space usage
  - find - search for files in a directory hierarchy
- Solution: cat ./-
- Password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
