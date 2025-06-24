# [Level 12 to 13](https://overthewire.org/wargames/natas/natas13.html) - Exploit file upload

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
  - Try it with a normal .png file
  ![image](https://github.com/user-attachments/assets/43cfa04b-895f-45a1-8557-ae839d16352e)
  ![image](https://github.com/user-attachments/assets/5a004dfe-cb4b-4528-bbd5-e1ec61a588dd)

  - Try it with a "fraud" .png file
  ```bash
    ┌──(kali㉿kali)-[~/Documents]
  └─$ echo '1' > test.png
                                                                                                                                                             
  ┌──(kali㉿kali)-[~/Documents]
  └─$ cat test.png        
  1
                                                                                                                                                             
  ┌──(kali㉿kali)-[~/Documents]
  └─$ file test.png
  test.png: ASCII text
  ```
  ![image](https://github.com/user-attachments/assets/300d86d4-e8e9-4079-bfc6-5d0476c86383)


- Password: `trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC`
