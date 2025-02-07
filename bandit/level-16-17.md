# [Level 16 to 17](https://overthewire.org/wargames/bandit/bandit17.html) - Port and Service Scanning with Nmap and SSL repetition

- Login
```
SSH: ssh bandit16@bandit.labs.overthewire.org -p 2220
Password: kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```
- Exercise: The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it. Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.
- Background:
  - Port scanner: Application designed to probe a server or host for open ports
  - ssh - OpenSSH remote login client
  - telnet - user interface to the TELNET protocol
  - nc - arbitrary TCP and UDP connections and listens
  - ncat - concatenate and redirect sockets
  - socat - multipurpose relay (SOcket CAT)
  - openssl - OpenSSL command line program
  - nmap - Network exploration tool and security / port scanner
  - netstat - print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships
  - ss - another utility to investigate sockets
- Solution:
  - Scansports from 31000 to 32000 on local machine, identify any services running on those ports, and attempt to determine their version
```
bandit16@bandit:~$ nmap -sV localhost -p 31000-32000
PORT      STATE    SERVICE     VERSION
31000/tcp filtered unknown
31046/tcp open     echo
31518/tcp open     ssl/echo
31691/tcp open     echo
31790/tcp open     ssl/unknown
31960/tcp open     echo

```
  - 5 ports are open, only two of those (31518 and 31790) use ssl, 31790 is the one we're looking for as this is the one that runs a unknown service
  - Use OpenSSL to connect to this port on localhost and send the password
```
bandit16@bandit:~$ echo "kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx" | openssl s_client -connect localhost:31790 -ign_eof
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```
  - Save the private key to `sshkey.private` and set permissions to user bandit17
```
bandit16@bandit:~$ mkdir /tmp/bandit42
bandit16@bandit:~$ cd /tmp/bandit42
bandit16@bandit:/tmp/bandit42$ nano sshkey.private
bandit16@bandit:/tmp/bandit42$ chmod 400 sshkey.private
bandit16@bandit:/tmp/bandit42$ ls -hal
total 17M
drwxrwxr-x 2 bandit16 bandit16 4.0K Feb  7 22:22 .
drwxrwx-wt 1 root     root      17M Feb  7 22:24 ..
-r-------- 1 bandit16 bandit16 1.7K Feb  7 22:22 sshkey.private
```
- Password: Private key
