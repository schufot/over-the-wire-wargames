# [Level 04 to 05](https://overthewire.org/wargames/bandit/bandit5.html) - File types, specifically human-readable files

- Login
```
SSH: ssh bandit4@bandit.labs.overthewire.org -p 2220
Password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```
- Exercise: The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
- Background:
  - ls - list directory contents
  - cd - change the working directory
  - cat - concatenate files and print on the standard output
  - file - determine file type
  - du - estimate file space usage
  - find - search for files in a directory hierarchy
- Solution:
  - cd inhere
  - file ./* - get type of all files
  - cat ./-file07
- Password: `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`
