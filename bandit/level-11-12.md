# [Level 11 to 12](https://overthewire.org/wargames/bandit/bandit12.html) - Rot13 substitution cipher as Linux command with ’tr’

- Login
```
SSH: ssh bandit11@bandit.labs.overthewire.org -p 2220
Password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
- Exercise: The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
- Background:
  - ROT13 is a letter substitution cipher that replaces a letter with the 13th letter after it in the Latin alphabet
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
- Solution: cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
  - cat data.txt - reads the content of the file data.txt and sends it to standard output (the terminal)
  - | (pipe) - takes the output from the command on the left (cat data.txt) and uses it as input for the command on the right (tr 'A-Za-z' 'N-ZA-Mn-za-m')
  - tr 'A-Za-z' 'N-ZA-Mn-za-m' - tr is used to translate or delete characters (first set of characters ('A-Za-z') specifies the input characters to be translated, which includes all uppercase and lowercase letters, second set of characters ('N-ZA-Mn-za-m') specifies the output characters)
  -> Each letter is replaced by the letter 13 positions down the alphabet. For example, 'A' becomes 'N', 'B' becomes 'O', ..., 'M' becomes 'Z', and then it wraps around (e.g., 'N' becomes 'A') (Same applies for lowercase letters)
- Password: `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`
