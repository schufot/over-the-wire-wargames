# [Level 30 to 31](https://overthewire.org/wargames/bandit/bandit30.html)- Git tagging
- Login
```
SSH: ssh bandit30@bandit.labs.overthewire.org -p 2220
Password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```
- Exercise: There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30. Clone the repository and find the password for the next level.
- Background:
  - git tagging: mark specific points in the history of the repository
- Solution:
```bash
bandit30@bandit:~$ mktemp -d
/tmp/tmp.z3KuA8ZDDo
bandit30@bandit:~$ cd /tmp/tmp.z3KuA8ZDDo
bandit30@bandit:/tmp/tmp.z3KuA8ZDDo$ git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
Cloning into 'repo'...
bandit30-git@localhost's password:
bandit30@bandit:/tmp/tmp.z3KuA8ZDDo/repo$ cat README.md
just an epmty file... muahaha
bandit30@bandit:/tmp/tmp.z3KuA8ZDDo/repo$ git tag
secret
bandit30@bandit:/tmp/tmp.z3KuA8ZDDo/repo$ git show secret
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```
- Password: `fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy`
