# [Level 15 to 16](https://overthewire.org/wargames/bandit/bandit16.html) - OpenSSL, secure communication

- Login
```
SSH: ssh bandit15@bandit.labs.overthewire.org -p 2220
Password: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```
- Exercise: The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption. Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.
- Background:
  - Transport Layer Security (TLS): Cryptographic protocol designed to provide communications security over a computer network
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
  - openssl s_client -connect localhost:30001
  - 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
- Password: `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`
