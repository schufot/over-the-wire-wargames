# [Level 00](https://overthewire.org/wargames/bandit/bandit0.html) - SSH login

- Login
```
SSH: ssh bandit0@bandit.labs.overthewire.org -p 2220
Password: bandit0
```
- Exercise: The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.
- Background:
  - Secure Shell (SSH) Protocol is a cryptographic network protocol for operating network services securely over an unsecured network
  - Most notable applications are remote login and command-line execution
  - Port is an endpoint that allows your computer to know which service should be accessed
  - ssh <username>@<server> -p <port>: server can be replaced with an URL or IP address, don't need to add port, if we connect to standard port 22
- Solution: ssh bandit0@bandit.labs.overthewire.org -p 2220
- Passsword: bandit0
