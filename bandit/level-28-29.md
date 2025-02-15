# [Level 28 to 29](https://overthewire.org/wargames/bandit/bandit29.html) - Git history

- Login
```
SSH: ssh bandit28@bandit.labs.overthewire.org -p 2220
Password: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
```
- Exercise: There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28. Clone the repository and find the password for the next level.
- Background:
  - git: version control system 
- Solution:
```bash
bandit28@bandit:~$ mktemp -d
/tmp/tmp.fYNkxDJgKw
bandit28@bandit:~$ cd /tmp/tmp.fYNkxDJgKw
bandit28@bandit:/tmp/tmp.fYNkxDJgKw$ git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
Cloning into 'repo'...
bandit28-git@localhost's password:
bandit28@bandit:/tmp/tmp.fYNkxDJgKw/repo$ git log
commit 817e303aa6c2b207ea043c7bba1bb7575dc4ea73 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Sep 19 07:08:39 2024 +0000

    fix info leak

commit 3621de89d8eac9d3b64302bfb2dc67e9a566decd
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Sep 19 07:08:39 2024 +0000

    add missing data

commit 0622b73250502618babac3d174724bb303c32182
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 19 07:08:39 2024 +0000

    initial commit of README.md
bandit28@bandit:/tmp/tmp.fYNkxDJgKw/repo$ git show 817e303aa6c2b207ea043c7bba1bb7575dc4ea73
commit 817e303aa6c2b207ea043c7bba1bb7575dc4ea73 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Sep 19 07:08:39 2024 +0000

    fix info leak

diff --git a/README.md b/README.md
index d4e3b74..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
+- password: xxxxxxxxxx
```
- Password: `4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7`
