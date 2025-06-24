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
  ![image](https://github.com/user-attachments/assets/24417e03-53af-4f51-9b64-08b9d67a0c86)



- Password: `trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC`
