# [Level 10 to 11](https://overthewire.org/wargames/natas/natas11.html) - XOR encryption

- Login
```
URL: http://natas11.natas.labs.overthewire.org
Username: natas11
Password: UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk
```
- Exercise:
![image](https://github.com/user-attachments/assets/8da7b4bd-60aa-4e93-b26f-d3f22abb3025)
![image](https://github.com/user-attachments/assets/7c223439-5835-4c91-8017-020bd66edae4)
![image](https://github.com/user-attachments/assets/f7293283-27d3-4400-900d-8c4667e21c8b)

- Background:
- Solution:

  ```php
  function xor_encrypt($in) {
      $key = '<censored>';
      $text = $in;
      $outText = '';
  
      // Iterate through each character
      for($i=0;$i<strlen($text);$i++) {
      $outText .= $text[$i] ^ $key[$i % strlen($key)];
      }
  
      return $outText;
  ```

  ``` php
  function saveData($d) {
      setcookie("data", base64_encode(xor_encrypt(json_encode($d))));
  }
  ```
- Password: `UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk`
