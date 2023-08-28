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
- Simpan private key dengan nama file **privatekey.pem**
```sh
echo 'paste privatekey disini' > id_rsa
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/wg%204.jpg)