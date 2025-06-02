# [Level 04 to 05](https://overthewire.org/wargames/natas/natas5.html) - HTTP-Cookies

- Login
```
URL: http://natas5.natas.labs.overthewire.org
Username: natas5
Password: 0n35PkggAPm2zbEpOU802c0x0Msn1ToK
```
- Exercise:
![image](https://github.com/user-attachments/assets/92b07762-abf9-49ee-b91c-18c898ef1746)
- Background:
  - HTTP is stateless:
    - No information about the session/previous requests is saved on the receivers/servers side
    - Client/browser saves session states and sends them with new requests
    - Session information is stored in cookies, allowing the otherwise stateless protocol to store and transfer stateful information
  - Cookies are sent with HTTP headers and are stored on the client side (client can manipulate them)
- Solution:
  - Website should determine that we're logged in through a cookie
  - ![image](https://github.com/user-attachments/assets/ec7f817c-bc0b-4a5a-aa1a-b8a3a81366dc)
  - Change loggedin value from 0 to 1
  - ![image](https://github.com/user-attachments/assets/08071521-7b99-4a2e-b451-f67725b813fb)
- Password: `0RoJwHdSKWFTYR5WuiAewauSuNaBXned`
