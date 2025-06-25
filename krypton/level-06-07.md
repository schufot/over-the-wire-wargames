# [Level 06-07](https://overthewire.org/wargames/krypton/krypton6.html) - Linear-feedback shift register

- Login
```
SSH: ssh krypton6@krypton.labs.overthewire.org -p 2231
Password: RANDOM
```
- Exercise:

  ```txt
  Hopefully by now its obvious that encryption using repeating keys is a bad idea. Frequency analysis can destroy repeating/fixed key substitution crypto.
  A feature of good crypto is random ciphertext. A good cipher must not reveal any clues about the plaintext. Since natural language plaintext (in this case, English) contains patterns, it is left up to the encryption key or the encryption algorithm to add the ‘randomness’.
  Modern ciphers are similar to older plain substitution ciphers, but improve the ‘random’ nature of the key.
  An example of an older cipher using a complex, random, large key is a vigniere using a key of the same size of the plaintext. For example, imagine you and your confident have agreed on a key using the book ‘A Tale of Two Cities’ as your key, in 256 byte blocks. The cipher works as such:
  Each plaintext message is broken into 256 byte blocks. For each block of plaintext, a corresponding 256 byte block from the book is used as the key, starting from the first chapter, and progressing. No part of the book is ever re-used as key. The use of a key of the same length as the plaintext, and only using it once is called a “One Time Pad”.
  Look in the krypton6 directory. You will find a file called ‘plain1’, a 256 byte block. You will also see a file ‘key1’, the first 256 bytes of ‘A Tale of Two Cities’. The file ‘cipher1’ is the cipher text of plain1. As you can see (and try) it is very difficult to break the cipher without the key knowledge.
  If the encryption is truly random letters, and only used once, then it is impossible to break. A truly random “One Time Pad” key cannot be broken. Consider intercepting a ciphertext message of 1000 bytes. One could brute force for the key, but due to the random key nature, you would produce every single valid 1000 letter plaintext as well. Who is to know which is the real plaintext?!?
  Choosing keys that are the same size as the plaintext is impractical. Therefore, other methods must be used to obscure ciphertext against frequency analysis in a simple substitution cipher. The impracticality of an ‘infinite’ key means that the randomness, or entropy, of the encryption is introduced via the method.
  We have seen the method of ‘substitution’. Even in modern crypto, substitution is a valid technique. Another technique is ‘transposition’, or swapping of bytes.
  Modern ciphers break into two types; symmetric and asymmetric.
  Symmetric ciphers come in two flavours: block and stream.
  Until now, we have been playing with classical ciphers, approximating ‘block’ ciphers. A block cipher is done in fixed size blocks (suprise!). For example, in the previous paragraphs we discussed breaking text and keys into 256 byte blocks, and working on those blocks. Block ciphers use a fixed key to perform substituion and transposition ciphers on each block discretely.
  Its time to employ a stream cipher. A stream cipher attempts to create an on-the-fly ‘random’ keystream to encrypt the incoming plaintext one byte at a time. Typically, the ‘random’ key byte is xor’d with the plaintext to produce the ciphertext. If the random keystream can be replicated at the recieving end, then a further xor will produce the plaintext once again.
  From this example forward, we will be working with bytes, not ASCII text, so a hex editor/dumper like hexdump is a necessity. Now is the right time to start to learn to use tools like cryptool.
  
- Background: Linear-feedback shift register
  - Shift register whose input bit is a linear function of its previous state
  - Most commonly used linear function of single bits is exclusive-or (XOR)
  - LFSR is most often a shift register whose input bit is driven by the XOR of some bits of the overall shift register value
- Solution:
  - HINT1:
  ```bash
  krypton6@bandit:/krypton/krypton6$ cat HINT1
  The 'random' generator has a limited number of bits, and is periodic.
  Entropy analysis and a good look at the bytes in a hex editor will help.

  There is a pattern!

  ```bash
  - Make a file in `/tmp` and use Python to fill it with 50 `A`s:
  ```bash
  krypton6@bandit:/krypton/krypton6$ mkdir /tmp/krypton6_tmp
  krypton6@bandit:/krypton/krypton6$ cd /tmp/krypton6_tmp
  krypton6@bandit:/tmp/krypton6_tmp$ touch test.txt
  krypton6@bandit:/tmp/krypton6_tmp$ python3 -c "print('A'*50)" > test.txt
  ```
  - Link the keyfile and run the encryption program:
  ```bash
  krypton6@bandit:/tmp/krypton6_tmp$ ln -s /krypton/krypton6/keyfile.dat 
  krypton6@bandit:/tmp/krypton6_tmp$ /krypton/krypton6/encrypt6 test.txt output.txt
  krypton6@bandit:/tmp/krypton6_tmp$ cat output.txt
  EICTDGYIYZKTHNSIRFXYCPFUEOCKRNEICTDGYIYZKTHNSIRFXY
  ```
  - Output repeats after a certain number of characters:
  ```txt
  EICTDGYIYZKTHNSIRFXYCPFUEOCKRN
  EICTDGYIYZKTHNSIRFX
  ```
  - Output for `B`s:
  ```txt
  FJDUEHZJZALUIOTJSGYZDQGVFPDLSO
  FJDUEHZJZALUIOTJSGY
  ```
  - `A->E`: Shift of 4 for the first letter
  - `A->I`: Shift of 8 for the second letter
  ```bash
  krypton6@bandit:/krypton/krypton6$ cat krypton7
  PNUKLYLWRQKGKBE
  ```
  - Python script to automate this:
  ```python
  import string
  
  cipher = "PNUKLYLWRQKGKBE"
  cipherlength = len(cipher)
  
  for i in range(0, cipherlength): 
      chosen = "AAAAAAAAAAAAAAA"
      encoded = "EICTDGYIYZKTHNS"
      print(ord(encoded[i]) - ord(chosen[i]))
  
  # the above prints: 4, 8, 2, 19, 3, 6, 24, 8, 24, 25, 10, 19, 7, 13, 18
  
  flag = ""
  decode = [4, 8, 2, 19, 3, 6, 24, 8, 24, 25, 10, 19, 7, 13, 18]
  
  for i in range(0, cipherlength): 
      char = ord(cipher[i]) # get the ciphertext character
      result = char - decode[i] # subtract to decode
      if (chr(result) not in string.ascii_letters): 
          result = char - decode[i] + 26
  
      flag += chr(result)
  
  print(flag)
  ```
- Password: `LFSRISNOTRANDOM`
