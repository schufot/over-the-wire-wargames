# [Level 05 to 06](https://overthewire.org/wargames/natas/natas6.html) - HTTP-Cookies

- Login
```
URL: http://natas6.natas.labs.overthewire.org
Username: natas6
Password: 0RoJwHdSKWFTYR5WuiAewauSuNaBXned
```
- Exercise:
![image](https://github.com/user-attachments/assets/fc9700e2-f2c5-4ed0-8a8c-fca73d90683e)
![image](https://github.com/user-attachments/assets/a2c50848-b7d6-44c8-8fe7-f0973b7cb608)
- Background:
  - PHP:
    - Scripting language
    - Back-end in web dev (meaning processed on server side)
    - Can be integrated in HTML (code will not be exposed to user)
    - In HTML enclosed in `<? ?>` or `<?php ?>`
    - Variables start with `$`
    - Content of forms sent with a POST request can be accessed with `$_POST` variable
    - Possible to include code from other files into a file using `include` or `require`
- Solution:
  - Website should determine that we're logged in through a cookie
  - ![image](https://github.com/user-attachments/assets/ec7f817c-bc0b-4a5a-aa1a-b8a3a81366dc)
  - Change loggedin value from 0 to 1 and refresh page
  - ![image](https://github.com/user-attachments/assets/08071521-7b99-4a2e-b451-f67725b813fb)
- Password: `0RoJwHdSKWFTYR5WuiAewauSuNaBXned`
