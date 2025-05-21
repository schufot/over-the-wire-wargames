# [Level 03 to 04](https://overthewire.org/wargames/natas/natas4.html) - HTML

- Login
```
URL: http://natas4.natas.labs.overthewire.org
Username: natas4
Password: QryZXc2e0zahULdHrtHxzyYkj59kUxLQ
```
- Exercise:
![image](https://github.com/user-attachments/assets/3e3b7184-4571-4626-933a-81aa8ee555ac)
![image](https://github.com/user-attachments/assets/d99c9d95-18d2-4f0e-a916-ff76c68e8efe)

- Background:
  - Communication between client (my machine) and server (hosts the website) is done by request-response: I send a request for a certain page and the server sends the response with content
  - Will follow different protocols and structures -> In this case HTTP (Hypertext Transfer Protocol): Request includes the request methd (GET, POST,...), the requested URL, the protocol version (can also include additional information, so-called request headers)
  - Relevant for this: Authorization and Referer (URL from which the request is sent)
  - All this is handled by browser, but you can manipulate it
- Solution:
  - Text on website seems to state that it's important from what page the link was requested -> Change the Referer header to the expected site
  - Open Developer Tools and go to Network and then refresh
  - You should see the requests that were sent
  - ![image](https://github.com/user-attachments/assets/a008e52e-63ab-4c1c-97c6-2004ab9526cc)
  - Right click on index.php > Copy Value > Copy cURL

```
  curl 'http://natas4.natas.labs.overthewire.org/index.php' --compressed -H 'User-Agent: Mozilla/5.0...
```

- Right click on index.php and click on Edit and Resend
- Add the line Referer: http://natas5.natas.labs.overthewire.org/
- 

- Password: `QryZXc2e0zahULdHrtHxzyYkj59kUxLQ`
