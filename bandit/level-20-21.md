# [Level 20 to 21](https://overthewire.org/wargames/bandit/bandit21.html) - Setuid binary, netcat and background processes/jobs

- Login
```
SSH: ssh bandit20@bandit.labs.overthewire.org -p 2220
Password: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```
- Exercise: There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21). NOTE: Try connecting to your own network daemon to see if it works as you think
- Background:
- Solution:
```bash
bandit20@bandit:~$ echo -n '0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO' | nc -l -p 1234 &
[1] 1841216
bandit20@bandit:~$ ./suconnect 1234
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
[1]+  Done                    echo -n '0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO' | nc -l -p 1234

```
- Password: `EeoULMCra2q0dSkYj561DX7s1CpBuOBt`
