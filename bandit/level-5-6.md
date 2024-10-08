# Level 5 to 6

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
- Password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
