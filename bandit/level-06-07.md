# [Level 06 to 07](https://overthewire.org/wargames/bandit/bandit7.html) - Find a file with specific user and group ownership

- Login
```
SSH: ssh bandit6@bandit.labs.overthewire.org -p 2220
Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```
- Exercise: The password for the next level is stored somewhere on the server and has all of the following properties:
  - owned by user bandit7
  - owned by group bandit6
  - 33 bytes in size
- Background:
  - ls - list directory contents
  - cd - change the working directory
  - cat - concatenate files and print on the standard output
  - file - determine file type
  - du - estimate file space usage
  - grep - searches for patterns in each file
- Solution:
  - find / -type f -user bandit7 -group bandit6 -size 33c -ls
    - find /: Starts a search from the root directory (/), looking through the entire filesystem
    - -type f: Tells find to look for files only (not directories)
    - -user bandit7 -group bandit6: Filters the results to include only files owned by the user bandit7 and group bandit6
    - -size 33c: Specifies that the file must be exactly 33 bytes in size (c indicates that the size is measured in bytes)
    - -ls: List the details of any files that meet these criteria
  - cat /var/lib/dpkg/info/bandit7.password
- Password: `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`
