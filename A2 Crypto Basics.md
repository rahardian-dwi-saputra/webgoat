# Base64 Encoding
- **Pertanyaan:** Authorization: Basic bXl1c2VyOm15cGFzc3dvcmQ=
```sh
echo 'dGVzdGluZzpwYXNzdzByZA==' | base64 --decode
``` 

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%201.JPG)

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

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%202.JPG)

**Jawaban:**
```sh
databasepassword
```

# Plain Hashing
- **Pertanyaan:**
	- 5F4DCC3B5AA765D61D8327DEB882CF99
	- 2BB80D537B1DA3E38BD30361AA855686BDE0EACD7162FEF6A25FE97BF527A25B
- Gunakan tool decrypt hash online https://crackstation.net/

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%203.JPG)

**Jawaban:**
```sh
password
secret
```

# RSA Private Key
- Simpan private key ke dalam sebuah file dengan nama **id_rsa**
```sh
echo 'paste privatekey disini' > id_rsa
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%204.jpg)

- Ambil public key dari private key dan simpan dengan nama file **id_rsa.pub**
```sh
openssl rsa -in id_rsa -pubout > id_rsa.pub
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%205.jpg)

- Ambil nilai modulus dari public key dan copy nilai modulus tersebut untuk menjawab soal
```sh
openssl rsa -in id_rsa.pub -pubin -modulus -noout
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%206.jpg)

- Ambil sign dari modulus dan private key dan simpan dengan nama file **sign.sha256**
```sh
echo -n "paste modulus disini" | openssl dgst -sign id_rsa -sha256 -out sign.sha256
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%207.jpg)

- Encode file **sign.sha256** dengan base64
```sh
openssl enc -base64 -in sign.sha256 -out sign.sha256.base64
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%208.jpg)

- Tampilkan isi file **sign.sha256.base64** dan copy isinya untuk menjawab soal
```sh
cat sign.sha256.base64
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%209.jpg)