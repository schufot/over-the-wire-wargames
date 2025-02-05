# [Level 05 to 06](https://overthewire.org/wargames/bandit/bandit6.html) - Human-readable files, file sizes and non-executable files

- Login
```
SSH: ssh bandit5@bandit.labs.overthewire.org -p 2220
Password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```
- Exercise: The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
    - human-readable
    - 1033 bytes in size
    - not executable
- Background:
  - ls - list directory contents
  - cd - change the working directory
  - cat - concatenate files and print on the standard output
  - file - determine file type
  - du - estimate file space usage
  - find - search for files in a directory hierarchy
- Solution:
  - cd inhere
  - ls -lhRsa (-l: use a long listing format, -h: human-readable, -R: list files with subdirectory, -s: size, -a: do not ignore entries starting with .)
  - cd maybeinhere07
  - cat .file2
- Password: `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`
