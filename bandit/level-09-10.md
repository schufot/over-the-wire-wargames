# [Level 09 to 10](https://overthewire.org/wargames/bandit/bandit10.html) - The ‘strings’ command. Find human-readable strings in a file

- Login
```
SSH: ssh bandit9@bandit.labs.overthewire.org -p 2220
Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```
- Exercise: The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters
- Background:
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
  - strings data.txt
- Password: `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`
