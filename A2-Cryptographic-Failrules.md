# Base64 Encoding
- **Pertanyaan:** Authorization: Basic bXl1c2VyOm15cGFzc3dvcmQ=
```sh
echo 'dGVzdGluZzpwYXNzdzByZA==' | base64 --decode
``` 

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/wg%201.JPG)

**Jawaban:**
- Username
```sh
testing
``` 
- Password
```sh
passw0rd
``` 

# XOR Encoding
- **Pertanyaan:** {xor}Oz4rPj0+LDovPiwsKDAtOw==
- Gunakan XOR decoder online https://strelitzia.net/wasXORdecoder/wasXORdecoder.html

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/wg%202.JPG)

**Jawaban:**
```sh
databasepassword
```

# Plain Hashing
- **Pertanyaan:**
	- 5F4DCC3B5AA765D61D8327DEB882CF99
	- 2BB80D537B1DA3E38BD30361AA855686BDE0EACD7162FEF6A25FE97BF527A25B
- Gunakan tool decrypt hash online https://crackstation.net/

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/wg%203.JPG)

**Jawaban:**
```sh
password
secret
```

# RSA Private Key
- **Pertanyaan:**
```sh
-----BEGIN PRIVATE KEY-----
MIIEvAIBADANBgkqhkiG9w0BAQEFAASCBKYwggSiAgEAAoIBAQDGZU9ZvsCuupJdignvvyt+DFCJm74CNmQeS47oDnFU6RjkGb8TO1CF9B417zI4BiKr7YuMVWVa7ZUzXi0z61DSoDu6DqkYa97zqPgNe4sY0XNwvC3KP5FeI/A8uH+lG/lC99nnUc7NLsUtvJvCD6qXVhdHJRPmmTFMWHYB6/J4/dvyTaC1LjHgyIcsRkqHikEyWxnkx9fWuLTjwRgldd4biSVwkpmXQ587Vw8N4pyyNJd2NZJsBxNGFUGTrH77kBPVvIuYT01s72geTFazsrqGkoevdOP+nsdEWIxMY8mnIThYlIhPth6jJEZOuXT1F6sj2RxM4JBD2BdaC0dHTa5TAgEDAoIBACEQ4o71IB0fGGTsVv1Khz+suBbvSlWzu1ph7SatEuN8LtCu9S3fOBZTWl5SiF6rsHH87JdjkOR87jM6XN38jXhwCfRXxtlnT9NG1AI/Qdl4PegfXPcKmDpbUrTJapuEqYspTvvi98zdINz0xKBX8cPjrovbg1EZiDdkE6r8qGl/WSzIHt/EJ7LS7MeNKBRfuXd4YMvQsWEY647KbZleqQvU3NpcC6O1smuSzRrgFfS+2E0Ls+xMGCtzlJ+9qWJOAhAzGj7Il1T1viLwufmUjHjAqaSbOPmZNcoB8Dsv51X4tDB1Dhzjp3PnwXArGTMNybxryGkhb/pALzgjrJiAVpMCgYEA+JNF7hN1XLW854gtqJYY5lvlnps/mJbQ8pol6uIVVfqMstkK7bJ7Kt0jIqAuLUkWTVZeKScmpePv/A2Q0kqBJUSh6lmr3bHzBA9K5GzDshwK57ENkn/sPhqV1aGef+KEyy1L7e+uG7FsPpZ501u72NsJ75X5cHzYI6wf0lKcBFkCgYEAzFJW+WMf5voaEvbJsXczAgmjNoKkFvlSPPDcm6sokdn/RXlfZg6GRdjDHcxz66ylOFGRMbsX3F1vyceptGM64i/oA8Xv47057z1dFm1zvZYDpiLD+6UbRm23FUel3cDINAiKRbKyFjpJfxc9CmcJF95IekAef+l+2F0VaWGvoosCgYEApbeD9Az46HkomlrJGw67RD1DvxIqZbngobwZR0FjjqcIdztcnnb8xz4XbGrJc4YO3jmUG29vGUKf/V5gjDGrbi3BRuZyk8v3WAox7Z3XzBKx78teYaqdfrxj48EUVUGt3MjdSUp0EnZIKbmmjOfSkJIGn7lQ9aiQF8gVNuG9WDsCgYEAiDbkpkIVRKa8DKSGdk93VrEXeaxtZKY200s9vRzFtpFU2PuU7rRZg+XXaTL38nMY0DZgy9IP6D5KhoUbzZd8lsqarS6f7SjRSijouZ5NKQ6tGWyCp8NnhEkkuNpuk9XazVsG2SHMDtGGVLoosZoGD+mFptVpqpup5ZNjm5Z1FwcCgYBf9W9ONc2yMe3cBhZ4VhuZqwJjsAcL4kMTFdL8YnkOhVgxCbU74bjJUlB3oMlsNgPEIeeX/nTkllKGmHTbqhvRcdYIuXBSbcKYVWNXxPXw8ceM9RjCn6EghJkz0JBoOVaeZMkqy1fiVHF92LtGmdfuFO8nvvSnaoPh3T+pgXkQlw==
-----END PRIVATE KEY-----
```

- Simpan private key dengan nama file **privatekey.pem**
```sh
echo 'paste privatekey disini' > privatekey.pem
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/wg%204.JPG)