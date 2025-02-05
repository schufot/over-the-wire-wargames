# [Level 03 to 04](https://overthewire.org/wargames/bandit/bandit4.html) - Hidden files

- Login
```
SSH: ssh bandit3@bandit.labs.overthewire.org -p 2220
Password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```
- Exercise: The password for the next level is stored in a hidden file in the inhere directory.
- Background:
  - ls - list directory contents
  - cd - change the working directory
    - cd.. - goes to parent directors
    - cd / - goes to root directory
    - cd ~ - goes to home directory 
  - cat - concatenate files and print on the standard output
  - file - determine file type
  - du - estimate file space usage
  - find - search for files in a directory hierarchy
- Solution:
  - cd inhere
  - cat ...Hiding-From-You
- Password: `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`
