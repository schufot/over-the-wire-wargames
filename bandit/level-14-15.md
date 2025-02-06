# [Level 14 to 15](https://overthewire.org/wargames/bandit/bandit15.html) - Netcat and first network communication

- Login
```
SSH: ssh bandit14@bandit.labs.overthewire.org -p 2220
Password: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```
- Exercise: The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
- Background:
  - [How the internet works](https://www.youtube.com/watch?v=7_LPdttKXPc):
    - Internet is a wire buried in the ground
    - Computers connected directly to the internet are called "Servers". Every server has a unique Internet Protocol Address (IP Address) and name (e. g. https://overthewire.org/wargames/).
    - Computers connected indirectly to the internet through a Internet Service Provider (ISP) are called "Clients".
    - Whenever an email, picture or webpage travels across the internet, computers break the information into smaller pieces, packets. When information reaches it's destination, packets are reensembled in their original order. 
    - How is the right destination found? Everything connected (in)directly to the internet has an IP address. Anywhere two or more parts of the internet intersect, routers direct packets around the internet helping each packet to get one step closer to it's destination. Everytime you visit a webpage upwards 10-15 routers may help your packets find their way to and from your computer.
    - Imagine each packet as a piece of candy wrapped in several layers: 1st layer is your computer's IP address, your computer sends the packet to the first router which adds it's own IP address. Each time the packet reaches a new router another layer is added until it reaches the server. Then when the server sends back information, it creates packets with an identical wrapping. As the packet makes it's way over the internet back to your computer each router unwraps a layer to discover where to send the packet next until it reaches your computer.
  - IP Address: Each machine on the internet is assigned a unique address called an IP address. IP stands for Internet protocol, and these addresses are 32-bit numbers, normally expressed as four "octets" in a dotted decimal number. A typical IP address looks like this: 216.27.61.137. The four numbers in an IP address are called octets because they can have values between 0 and 255, which is 28 possibilities per octet. A server has a static IP address that does not change very often. A home machine that is dialing up through a modem often has an IP address that is assigned by the ISP when the machine dials in. That IP address is unique for that session -- it may be different the next time the machine dials in. This way, an ISP only needs one IP address for each modem it supports, rather than for each customer.
  - Ports: Any server machine makes its services available to the Internet using numbered ports, one for each service that is available on the server. For example, if a server machine is running a Web server and an FTP server, the Web server would typically be available on port 80, and the FTP server would be available on port 21. Clients connect to a service at a specific IP address and on a specific port.
  - ssh - OpenSSH remote login client
  - telnet - user interface to the TELNET protocol
  - nc - arbitrary TCP and UDP connections and listens
  - openssl - OpenSSL command line program
  - nmap - Network exploration tool and security / port scanner
- Solution: echo "MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS" | nc localhost 30000
- Password: `8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`
