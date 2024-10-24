# [Level 13 to 14](https://overthewire.org/wargames/bandit/bandit14.html)

- Exercise: The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on
- Background:
  - PKA: Authenticating entity has a public key and a private key (= large number), private key is kept on the computer you log in from while the public key is stored on the .ssh/authorized_keys file on all the computers you want to log in to
	- When you log in to a computer, the SSH server uses the public key to "lock" messages in a way that can only be "unlocked" by your private key  
  - ssh - OpenSSH remote login client
  - telnet - user interface to the TELNET protocol
  - nc - arbitrary TCP and UDP connections and listens
  - openssl - OpenSSL command line program
  - nmap - Network exploration tool and security / port scanner
- Solution: ssh -i '/home/bandit13/sshkey.private' bandit14@bandit.labs.overthewire.org -p 2220
- Password: /
