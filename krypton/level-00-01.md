# [Level 00-01](https://overthewire.org/wargames/krypton/krypton0.html) - Base64

- Login
```
SSH: ssh krypton1@krypton.labs.overthewire.org -p 2231
Password: KRYPTONISGREAT
```
- Exercise: Welcome to Krypton! The first level is easy. The following string encodes the password using Base64: `S1JZUFRPTklTR1JFQVQ=` Use this password to log in to krypton.labs.overthewire.org with username krypton1 using SSH on port 2231. You can find the files for other levels in /krypton/
- Background:
  - Base64: group of binary-to-text encoding schemes that transforms binary data into a sequence of printable characters, limited to a set of 64 unique characters
- Solution:
  - Decode using base64: `S1JZUFRPTklTR1JFQVQ=` -> `KRYPTONISGREAT` 
- Password: `KRYPTONISGREAT`
