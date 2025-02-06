# [Level 10 to 11](https://overthewire.org/wargames/bandit/bandit11.html) - Base64

- Login
```
SSH: ssh bandit10@bandit.labs.overthewire.org -p 2220
Password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```
- Exercise: The password for the next level is stored in the file data.txt, which contains base64 encoded data
- Background:
  - Base64 encodes (binary) data; the resulting Base64 data will only contain 64 different ASCII characters
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
  - base64 data.txt -d
- Password: `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`
