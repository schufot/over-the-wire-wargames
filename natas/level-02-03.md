# [Level 02 to 03](https://overthewire.org/wargames/natas/natas3.html) - HTML

- Login
```
URL: http://natas3.natas.labs.overthewire.org
Username: natas3
Password: 3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH
```
- Exercise: There is nothing on this page
- Background:
- Solution:
  - ![image](https://github.com/user-attachments/assets/72e3be3e-c0cf-4bf6-a5b9-1f923b1f4624)
  - `http://natas3.natas.labs.overthewire.org/robots.txt` gives
```txt
User-agent: *
Disallow: /s3cr3t/
```
  - `http://natas3.natas.labs.overthewire.org/s3cr3t/` has `users.txt` file
```txt
natas4:QryZXc2e0zahULdHrtHxzyYkj59kUxLQ
```
- Password: `QryZXc2e0zahULdHrtHxzyYkj59kUxLQ`
