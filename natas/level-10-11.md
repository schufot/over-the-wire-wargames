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
  - Get the cookie value: `HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg`
  - ![image](https://github.com/user-attachments/assets/1a88c2b7-0fc0-4603-944c-7229e11cb20e)
  - Run the following with the cookie value:
  ```php
  <?php  
  $defaultdata = array( "showpassword"=>"no", "bgcolor"=>"#ffffff");
  function xor_encrypt($in) {
      $key = base64_decode('HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg%3D');
      $text = $in;
      $outText = '';
  
      // Iterate through each character
      for($i=0;$i<strlen($text);$i++) {
      $outText .= $text[$i] ^ $key[$i % strlen($key)];
      }
  
      return $outText;
  }  
  $key = xor_encrypt(json_encode($defaultdata));  
  print "The XOR key is " . $key . "\n"
  ?>
  ```
  - Output: `The XOR key is eDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoe`
  - The run:
  ```php
  <?php  
  $defaultdata = array( "showpassword"=>"yes", "bgcolor"=>"#ffffff");
  function xor_encrypt($in) {
      $key = 'eDWo';
      $text = $in;
      $outText = '';
  
      // Iterate through each character
      for($i=0;$i<strlen($text);$i++) {
      $outText .= $text[$i] ^ $key[$i % strlen($key)];
      }
  
      return $outText;
  }  
  $new_cookie = base64_encode(xor_encrypt(json_encode($defaultdata)));  
  print "The new cookie is " . $new_cookie . "\n"
  ?>
  ```
  - Output: `The new cookie is HmYkBwozJw4WNyAAFyB1VUc9MhxHaHUNAic4Awo2dVVHZzEJAyIxCUc5`
  - Set this new value as the cookie value and reload
  - ![image](https://github.com/user-attachments/assets/07eb47cb-4693-4963-a176-1a73f0e43ba4)
- Password: `yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB`
