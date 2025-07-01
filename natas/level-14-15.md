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
- Solution:
 - Source code explanation:
   - If `username` is included in the request, connect to the database, and `SELECT` all from table users where the username = user input
   - If the debug key exists on the request, show the query to the user
   - If the number of rows is greater than 0, say that the user exists


- Password: `SdqIqBsFcz3yotlNYErZSZwblkm0lrvx`
