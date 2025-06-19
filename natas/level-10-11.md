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
  $defaultdata = array( "showpassword"=>"nyes", "bgcolor"=>"#ffffff");
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
- Password: `UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk`
