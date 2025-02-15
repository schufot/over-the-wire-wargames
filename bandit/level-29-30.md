# [Level 29 to 30](https://overthewire.org/wargames/bandit/bandit30.html)- Git branching basics

- Login
```
SSH: ssh bandit29@bandit.labs.overthewire.org -p 2220
Password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
```
- Exercise: There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29. Clone the repository and find the password for the next level.
- Background:
  - git: version control system 
- Solution:
```bash
bandit29@bandit:~$ mktemp -d
/tmp/tmp.JxGaPGfEOl
bandit29@bandit:~$ cd /tmp/tmp.JxGaPGfEOl
bandit29@bandit:/tmp/tmp.JxGaPGfEOl$ git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
Cloning into 'repo'...
bandit29-git@localhost's password: 
bandit29@bandit:/tmp/tmp.JxGaPGfEOl/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
bandit29@bandit:/tmp/tmp.JxGaPGfEOl/repo$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
bandit29@bandit:/tmp/tmp.JxGaPGfEOl/repo$ git checkout remotes/origin/dev
bandit29@bandit:/tmp/tmp.JxGaPGfEOl/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```
- Password: `qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL`
