# [Level 27 to 28](https://overthewire.org/wargames/bandit/bandit28.html) - Git introduction and basics

- Login
```
SSH: ssh bandit27@bandit.labs.overthewire.org -p 2220
Password: upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
```
- Exercise: There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27. Clone the repository and find the password for the next level.
- Background:
  - git: version control system 
- Solution:
```bash
bandit27@bandit:~$ mktemp -d
/tmp/tmp.YPJwnuE31t
bandit27@bandit:~$ cd /tmp/tmp.YPJwnuE31t
bandit27@bandit:/tmp/tmp.YPJwnuE31t$ git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
Cloning into 'repo'...
bandit27-git@localhost's password:
bandit27@bandit:/tmp/tmp.YPJwnuE31t$ cd repo
bandit27@bandit:/tmp/tmp.YPJwnuE31t/repo$ ls
README
bandit27@bandit:/tmp/tmp.YPJwnuE31t/repo$ cat README
The password to the next level is: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
```
- Password: `Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN`
