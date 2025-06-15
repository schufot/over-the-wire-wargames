# [Level 07 to 08](https://overthewire.org/wargames/natas/natas8.html) - Hex, reverse, base64

- Login
```
URL: http://natas8.natas.labs.overthewire.org
Username: natas8
Password: xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q
```
- Exercise:
![image](https://github.com/user-attachments/assets/0dc6ff34-dea9-4fe6-aacd-4d26835758fd)
![image](https://github.com/user-attachments/assets/8fa99854-014b-43ce-9597-f44713e7e2a2)
- Background:
    - Hexadecimal: Positional numeral system that represents numbers using a radix (base) of sixteen
    - strrev: Return string in reverse order
    - Base64: Group of binary-to-text encoding schemes that transforms binary data into a sequence of printable characters, limited to a set of 64 unique characters
- Solution:

```php
$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}
```
  - `encodeSecret` function:
   1. Encodes the input string using `base64_encode()`
   2. Reverses the result with `strrev()`
   3. Converts the reversed string into hexadecimal using `bin2hex()`
 - To pass the `if` condition, we need to reverse this encoding process to find the correct `$_POST['secret']` that would match with `$encodedSecret`
 - We want to decode this:

```php
$encodedSecret = "3d3d516343746d4d6d6c315669563362";
```
 1. Convert hex to raw string

```php
$hex = "3d3d516343746d4d6d6c315669563362";
$bin = hex2bin($hex);  // reversed base64 string: ==QcCtmMml1ViV3b
```

 2. Reverse the string

```php
strrev("==QcCtmMml1ViV3b") = "b3ViV1lmMmtCcQ=="
```

 3. Base64 decode

```php
base64_decode("b3ViV1lmMmtCcQ==") = "oubWYf2kBq"
```

4. Access granted. The password for natas9 is ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t
- Password: `ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t`
