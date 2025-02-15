# [Level 31 to 32](https://overthewire.org/wargames/bandit/bandit31.html)- Git push, commit, ignore, add
- Login
```
SSH: ssh bandit31@bandit.labs.overthewire.org -p 2220
Password: fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```
- Exercise: There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31. Clone the repository and find the password for the next level.
- Background:
  - git tagging: mark specific points in the history of the repository
- Solution:
```bash
bandit31@bandit:~$ mktemp -d
/tmp/tmp.ZBlkdaybn2
bandit31@bandit:~$ cd /tmp/tmp.ZBlkdaybn2
bandit31@bandit:/tmp/tmp.ZBlkdaybn2$ git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
Cloning into 'repo'...
bandit31-git@localhost's password:
bandit31@bandit:/tmp/tmp.ZBlkdaybn2/repo$ cat README.md
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
bandit31@bandit:/tmp/tmp.ZBlkdaybn2/repo$ echo 'May I come in?' > key.txt
bandit31@bandit:/tmp/tmp.ZBlkdaybn2/repo$ cat key.txt
May I come in?
bandit31@bandit:/tmp/tmp.ZBlkdaybn2/repo$ cat .gitignore
*.txt
```
  - Use `f` flag to force file to be able to be committed, even when they are normally ignored
```bash
bandit31@bandit:/tmp/tmp.ZBlkdaybn2/repo$ git add -f key.txt
bandit31@bandit:/tmp/tmp.ZBlkdaybn2/repo$ git commit -a
Unable to create directory /home/bandit31/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

[master 31f4c6c] 42
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt
bandit31@bandit:/tmp/tmp.ZBlkdaybn2/repo$ git push -u origin master
bandit31-git@localhost's password: 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 2 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 317 bytes | 317.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: ### Attempting to validate files... ####
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
remote: Well done! Here is the password for the next level:
remote: 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K 
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
```
- Password: `3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K`
