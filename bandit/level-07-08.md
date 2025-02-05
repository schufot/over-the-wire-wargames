# [Level 07 to 08](https://overthewire.org/wargames/bandit/bandit8.html) - Learning grep and piping

- Login
```
SSH: ssh bandit7@bandit.labs.overthewire.org -p 2220
Password: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```
- Exercise: The password for the next level is stored in the file data.txt next to the word millionth
- Background:
  - man - an interface to the system reference manuals
  - grep - searches for patterns in each file
  - sort - sort lines of text files
  - uniq - report or omit repeated lines
  - strings - print the sequences of printable characters in files
  - base64 - base64 encode/decode data and print to standard output
  - tr - translate or delete characters
  - tar - an archiving utility
  - gzip - compress or expand files
  - bzip2 - a block-sorting file compressor
  - xxd - make a hex dump or do the reverse
- Solution:
  - grep millionth data.txt
- Password: `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`
