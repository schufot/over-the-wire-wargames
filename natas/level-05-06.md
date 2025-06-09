# [Level 05 to 06](https://overthewire.org/wargames/natas/natas6.html) - PHP

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
  - HTML form shows what happens with the input: POST request is used to send the input with the variable name `secret`
  - PHP part processes this information, POST request is checked for a variable with the name `submit`
  - If the variable exists, content or the inputed `secret` variable `$_POST['secret']` is compared to a variable called `secret`
  - However, code does not contain an un/initialized variable with this name -> But contains `include` statement (variables or functions are included from another file, statement shows a relative path to the file)
  - Visit http://natas6.natas.labs.overthewire.org/includes/secret.inc and get the password
  - ![image](https://github.com/user-attachments/assets/69de6f22-1716-4156-9004-3499ef289562)
  - ![image](https://github.com/user-attachments/assets/5c41609e-8b4a-43e7-855d-f024f54c7269)
- Password: `bmg8SvU1LizuWjx3y7xkNERkHxGre0GS`
