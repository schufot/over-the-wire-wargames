# [Level 06 to 07](https://overthewire.org/wargames/natas/natas7.html) - PHP script

- Login
```
URL: http://natas7.natas.labs.overthewire.org
Username: natas7
Password: bmg8SvU1LizuWjx3y7xkNERkHxGre0GS
```
- Exercise:
![image](https://github.com/user-attachments/assets/356d97b2-ee9d-4946-aca9-9f3f47d55f8f)
![image](https://github.com/user-attachments/assets/adb2c5c5-4f55-4ad9-825a-edfeb1e938c8)

- Background:
  - `http://natas7.natas.labs.overthewire.org/index.php?page=home`:
    - `index.php`: PHP file that will be executed on the server
    - `?page=home`: Query string, starting with `?`, used to pass information to the script
    - PHP file `index.php`receives a GET parameter named `page` with the value `home`
    - Script may then use this value to determine what content to display
    - Instead of having separate physical files like `home.html`, `about.html` etc., a single PHP file controls which content to display based on the query string
- Solution:
  - Set end of URL to `page=password`
  - ![image](https://github.com/user-attachments/assets/0cea9c08-5777-49d5-be42-7610c0248b9d) -> Hint gets displayed
  - ![image](https://github.com/user-attachments/assets/c34696a9-8912-4c37-a27d-f324ef22edc5)
- Password: `xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q`
