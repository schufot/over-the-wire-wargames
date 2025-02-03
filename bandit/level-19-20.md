# [Level 19 to 20](https://overthewire.org/wargames/bandit/bandit20.html)

- Login
```
SSH: ssh bandit19@bandit.labs.overthewire.org -p 2220
Password: IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```
- Exercise: To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.
- Background:
  - `setuid` and `setgid` (short for set user identity and set group identity) allow users to run an executable with the file system permissions of the executable's owner or group respectively and to change behaviour in directories
- Solution:
  - ls -la: check who the owner of the of the setuid binary is (owner is bandit20 and the group is bandit19, user bandit19 can execute the binary, but the binary is executed as user bandit20)
  - ./bandit20-do
  - ./bandit20-do id
  - ./bandit20-do ls /etc/bandit_pass
  - ./bandit20-do cat /etc/bandit_pass/bandit20
- Password: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
