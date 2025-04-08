# [Level 01 to 02](https://overthewire.org/wargames/natas/natas2.html) - Web server files

- Login
```
URL: http://natas2.natas.labs.overthewire.org
Username: natas2
Password: TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI
```
- Exercise: There is nothing on this page
- Background:
  - Server: Computer that allows requests and sends responses to a client
  - Web server: Sends files requested through a URL (main part of the URL can be seen as address of the server, while anything following it is the location of a file on the server
  - Website should allow acess to files, but not to folders (otherwise all files in the folders would be known and accessible)
  - Websites are set up with HTML, CSS and JavaScript files
  - Web server can host other types of files which are either embedded in a website or accessible on their own through the correct path
- Solution:
  - Find image under `http://natas2.natas.labs.overthewire.org/files/pixel.png`
  - In folder `files` is `users.txt` (`http://natas2.natas.labs.overthewire.org/files/`)
```txt
# username:password
alice:BYNdCesZqW
bob:jw2ueICLvT
charlie:G5vCxkVV3m
natas3:3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH
eve:zo4mJWyNj2
mallory:9urtcpzBmH
```
- Password: `3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH`
