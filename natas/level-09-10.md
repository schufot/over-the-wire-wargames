# [Level 09 to 10](https://overthewire.org/wargames/natas/natas10.html) - Command injection with filtering

- Login
```
URL: http://natas10.natas.labs.overthewire.org
Username: natas10
Password: t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu
```
- Exercise:
![image](https://github.com/user-attachments/assets/28feaf2b-7da8-4bc8-8ed4-10638e1f5cc5)
![image](https://github.com/user-attachments/assets/a963c2bd-767f-4ce2-b1d8-b1012d02c02e)

- Background:
  - Command injection:
    - Attack in which the goal is execution of arbitrary commands on the host operating system via a vulnerable application
    - Possible when an application passes unsafe user supplied data (forms, cookies, HTTP headers etc.) to a system shell
    - Attacker-supplied operating system commands are usually executed with the privileges of the vulnerable application
    - Possible largely due to insufficient input validation
- Solution:
  - Executes a shell command using user input `$key`, after filtering for three characters:
  ``` php
  if(preg_match('/[;|&]/',$key)) {
    print "Input contains an illegal character!";
  ```
  - `;`, `|` and `&` are blocked, but we can still inject commands like `''` and `...`
  - Enter in input field: `'' /etc/natas_webpass/natas11`
  - ![image](https://github.com/user-attachments/assets/00921a6b-a526-44cb-8624-92a00143c50d)

- Password: `UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk`
