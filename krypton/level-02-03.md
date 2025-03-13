# [Level 02-03](https://overthewire.org/wargames/krypton/krypton2.html) - ROT13

- Login
```
SSH: ssh krypton2@krypton.labs.overthewire.org -p 2231
Password: ROTTEN
```
- Exercise: ROT13 is a simple substitution cipher. Substitution ciphers are a simple replacement algorithm. In this example of a substitution cipher, we will explore a ‘monoalphebetic’ cipher. Monoalphebetic means, literally, “one alphabet” and you will see why.
This level contains an old form of cipher called a ‘Caesar Cipher’. A Caesar cipher shifts the alphabet by a set number. For example:
plain:  a b c d e f g h i j k ...
cipher: G H I J K L M N O P Q ...
In this example, the letter ‘a’ in plaintext is replaced by a ‘G’ in the ciphertext so, for example, the plaintext ‘bad’ becomes ‘HGJ’ in ciphertext. The password for level 3 is in the file krypton3. It is in 5 letter group ciphertext. It is encrypted with a Caesar Cipher. Without any further information, this cipher text may be difficult to break. You do not have direct access to the key, however you do have access to a program that will encrypt anything you wish to give it using the key. If you think logically, this is completely easy.
One shot can solve it!
Have fun.
Additional Information: The encrypt binary will look for the keyfile in your current working directory. Therefore, it might be best to create a working direcory in /tmp and in there a link to the keyfile. As the encrypt binary runs setuid krypton3, you also need to give krypton3 access to your working directory.
  ```
  krypton2@melinda:~$ mktemp -d
  /tmp/tmp.Wf2OnCpCDQ
  krypton2@melinda:~$ cd /tmp/tmp.Wf2OnCpCDQ
  krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ln -s /krypton/krypton2/keyfile.dat
  krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
  keyfile.dat
  krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ chmod 777 .
  krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ /krypton/krypton2/encrypt /etc/issue
  krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
  ciphertext  keyfile.dat
  ```
- Background:
  - One of the simplest and most widely known encryption techniques, type of substitution cipher in which each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabetafter it in the alphabet
- Solution:
```bash
krypton2@bandit:/home$ cat /krypton/krypton2/krypton3
OMQEMDUEQMEK
krypton2@bandit:/home$ mktemp -d
/tmp/tmp.EO14qQ7WZt
krypton2@bandit:/home$ cd /tmp/tmp.EO14qQ7WZt
krypton2@bandit:/tmp/tmp.EO14qQ7WZt$ chmod 777 .
krypton2@bandit:/tmp/tmp.EO14qQ7WZt$ touch solution.py
krypton2@bandit:/tmp/tmp.EO14qQ7WZt$ nano solution.py
krypton2@bandit:/tmp/tmp.EO14qQ7WZt$ cat solution.py
import string
charset = string.ascii_uppercase
enc = "OMQEMDUEQMEK"
for k in range(26):
        dec = ""
        for c in enc:
                if c in charset:
                        idx = charset.find(c)
                        idx += k
                        if idx >= len(charset):
                                idx -= len(charset)
                        elif idx < 0:
                                idx += len(charset)
                        dec += charset[idx]
                else:
                        dec = dec + c
        print(dec)
krypton2@bandit:/tmp/tmp.EO14qQ7WZt$ python3 solution.py
OMQEMDUEQMEK
PNRFNEVFRNFL
QOSGOFWGSOGM
RPTHPGXHTPHN
SQUIQHYIUQIO
TRVJRIZJVRJP
USWKSJAKWSKQ
VTXLTKBLXTLR
WUYMULCMYUMS
XVZNVMDNZVNT
YWAOWNEOAWOU
ZXBPXOFPBXPV
AYCQYPGQCYQW
BZDRZQHRDZRX
CAESARISEASY
DBFTBSJTFBTZ
ECGUCTKUGCUA
FDHVDULVHDVB
GEIWEVMWIEWC
HFJXFWNXJFXD
IGKYGXOYKGYE
JHLZHYPZLHZF
KIMAIZQAMIAG
LJNBJARBNJBH
MKOCKBSCOKCI
NLPDLCTDPLDJ
```
- Password: `CAESARISEASY`
