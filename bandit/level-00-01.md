# [Level 00 to 01](https://overthewire.org/wargames/bandit/bandit1.html) - Read a file

- Login
```
SSH: ssh bandit0@bandit.labs.overthewire.org -p 2220
Password: bandit0
```
- Exercise: The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
- Background:
  - ls - list directory contents
  - cd - change the working directory
  - cat - concatenate files and print on the standard output
  - file - determine file type
  - du - estimate file space usage
  - find - search for files in a directory hierarchy
- Solution: cat readme
- Password: `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`
