# [Level 02 to 03](https://overthewire.org/wargames/natas/natas3.html) - Robots

- Login
```
URL: http://natas3.natas.labs.overthewire.org
Username: natas3
Password: 3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH
```
- Exercise: There is nothing on this page
- Background:
  - Internet is indexed by search-engine crawlers -> Google and Co know what content exists on websites to improve search engine results
  - `robots.txt` file exists on servers to tell these crawlers and other web bots, which part of the website can be visited. It allows defining an user-agent (= for what specific bot the rules should be) and which page of the website the user-agent is not allowed to visit
  - Example
  ```txt
  User-agent: Googlebot
  Disallow: /nogooglebot/

  User-agent: *
  Allow: /

  Sitemap: https://www.example.com/sitemap.xml
  ```
  - All crawlers/bots can visit the website, except Google's crawler which cannot visit the `nogooglebot` directory
  - Sitemap link is another file that gives web crawlers information about the website
- Solution:
  - ![image](https://github.com/user-attachments/assets/72e3be3e-c0cf-4bf6-a5b9-1f923b1f4624)
  - `http://natas3.natas.labs.overthewire.org/robots.txt` gives
```txt
User-agent: *
Disallow: /s3cr3t/
```
  - `http://natas3.natas.labs.overthewire.org/s3cr3t/` has `users.txt` file
```txt
natas4:QryZXc2e0zahULdHrtHxzyYkj59kUxLQ
```
- Password: `QryZXc2e0zahULdHrtHxzyYkj59kUxLQ`
