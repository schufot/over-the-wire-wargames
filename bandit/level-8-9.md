# [Level 8 to 9](https://overthewire.org/wargames/bandit/bandit9.html)

- Exercise: The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
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
  - cat data.txt | sort | uniq -u
- Password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM