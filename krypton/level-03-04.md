# [Level 03-04](https://overthewire.org/wargames/krypton/krypton3.html) - ROT13

- Login
```
SSH: ssh krypton3@krypton.labs.overthewire.org -p 2231
Password: CAESARISEASY
```
- Exercise: Well done. You’ve moved past an easy substitution cipher. The main weakness of a simple substitution cipher is repeated use of a simple key. In the previous exercise you were able to introduce arbitrary plaintext to expose the key. In this example, the cipher mechanism is not available to you, the attacker. However, you have been lucky. You have intercepted more than one message. The password to the next level is found in the file ‘krypton4’. You have also found 3 other files. (found1, found2, found3). You know the following important details: The message plaintexts are in American English (*** very important) - They were produced from the same key (*** even better!). Enjoy.
- Background:
- Solution:
  ```bash
  krypton3@bandit:~$ cd /krypton/krypton3
  krypton3@bandit:/krypton/krypton3$ ls
  found1  found2  found3  HINT1  HINT2  krypton4  README
  krypton3@bandit:/krypton/krypton3$ cat README
  Well done.  You've moved past an easy substitution cipher.
  
  Hopefully you just encrypted the alphabet a plaintext 
  to fully expose the key in one swoop.
  
  The main weakness of a simple substitution cipher is 
  repeated use of a simple key.  In the previous exercise
  you were able to introduce arbitrary plaintext to expose
  the key.  In this example, the cipher mechanism is not 
  available to you, the attacker.
  
  However, you have been lucky.  You have intercepted more
  than one message.  The password to the next level is found
  in the file 'krypton4'.  You have also found 3 other files.
  (found1, found2, found3)
  
  You know the following important details:
  
  - The message plaintexts are in English (*** very important)
  - They were produced from the same key (*** even better!)
  
  
  Enjoy.
  ```
- Password: `CAESARISEASY`
