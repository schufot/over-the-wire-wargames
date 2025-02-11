# [Level 25 to 26](https://overthewire.org/wargames/bandit/bandit26.html) - Breaking out of a restricted environment with more and vim

- Login
```
SSH: ssh bandit25@bandit.labs.overthewire.org -p 2220
Password: iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
```
- Exercise: Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it. NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.
- Background:
  - Each user has a user default shell -> Can be found a the `/etc/passwd` file
- Solution:
  - Check what shell bandit26 uses
```bash
bandit25@bandit:~$ cat /etc/passwd | grep bandit26
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
bandit25@bandit:~$ ls -la /usr/bin/showtext
-rwxr-xr-x 1 root root 58 Sep 19 07:08 /usr/bin/showtext
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```
  - Use private key
```bash
bandit24@bandit:~$ mktemp -d
/tmp/tmp.GnsTBgHerI
bandit24@bandit:~$ cd /tmp/tmp.GnsTBgHerI
bandit24@bandit:/tmp/tmp.GnsTBgHerI$ nano brute_force_pin.sh
bandit24@bandit:/tmp/tmp.GnsTBgHerI$ cat brute_force_pin.sh
#!/bin/bash

for i in {0000..9999}
do
        echo gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i >> possibilities.txt
done

cat possibilities.txt | nc localhost 30002 > result.txt
bandit24@bandit:/tmp/tmp.GnsTBgHerI$ chmod +x brute_force_pin.sh
bandit24@bandit:/tmp/tmp.GnsTBgHerI$ ./brute_force_pin.sh 
bandit24@bandit:/tmp/tmp.GnsTBgHerI$ ls
brute_force_pin.sh  possibilities.txt  result.txt
bandit24@bandit:/tmp/tmp.GnsTBgHerI$ sort result.txt | grep -v "Wrong!"

Correct!
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
The password of user bandit25 is iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
```
- Password: `iCi86ttT4KSNe1armKiwbQNmB3YJP3q4`
