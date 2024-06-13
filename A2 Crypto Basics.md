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

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%205.JPG)

- Ambil nilai modulus dari public key dan copy nilai modulus tersebut untuk menjawab soal
```sh
openssl rsa -in id_rsa.pub -pubin -modulus -noout
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%206.JPG)

- Ambil sign dari modulus dan private key dan simpan dengan nama file **sign.sha256**
```sh
echo -n "paste modulus disini" | openssl dgst -sign id_rsa -sha256 -out sign.sha256
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%207.JPG)

- Encode file **sign.sha256** dengan base64
```sh
openssl enc -base64 -in sign.sha256 -out sign.sha256.base64
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%208.JPG)

- Tampilkan isi file **sign.sha256.base64** dan copy isinya untuk menjawab soal
```sh
cat sign.sha256.base64
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%209.JPG)

# Java cacerts
- Jalankan docker image terlebih dahulu di mesin Ubuntu. Jika docker image belum tersedia maka sistem akan mendownload secara otomatis. Jika sudah akan tampil hash id untuk mengakses docker shell
```sh
sudo docker run -d webgoat/assignments:findthesecret
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%2010.JPG)

- Akses docker shell melalui terminal
```sh
sudo docker exec -it docker_id /bin/bash
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%2011.JPG)

- Kita tidak dapat mengakses direktori `/root` tapi kita bisa mengakses direktori `/etc` dan menemukan file `passwd` disana
```sh
cd /etc
ls
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%2012.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%2013.JPG)

- Baca isi file `passwd` lalu ketik `exit` untuk keluar dari docker shell
```sh
cat passwd
exit
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%2014.JPG)

- Sekarang kita copy file `/etc/passwd` dari docker ke lokal
```sh
sudo docker cp docker_id:/etc/passwd ./passwd
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%2015.JPG)

- Edit file `passwd` dengan editor nano. Lalu ubah user ID (uid) dan grup ID (gid) user webgoat menjadi 0 sehingga mempunyai akses user root. Tekan `Ctrl+O` untuk menyimpan dan tekan `Ctrl+X` untuk keluar 
```sh
sudo nano passwd
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%2016.JPG)

- Masukkan file `passwd` yang sudah dimodifikasi ke docker shell
```sh
sudo docker cp ./passwd docker_id:/etc/passwd
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%2017.JPG)

- Akses docker shell kembali melalui terminal dan sekarang kita berhasil masuk sebagai user root
```sh
sudo docker exec -it docker_id /bin/bash
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%2018.JPG)

- Akses direktori `/root` dan disana terdapat file `default_secret` yang berisi key yang akan kita gunakan untuk mendekrip pesan di task ini
```sh
cd /root
cat default_secret
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%2019.JPG)

- Sekarang kita tahu bahwa file yang menyimpan key bernama `default_secret` jadi kita tinggal masukkan nama file tersebut ke dalam command line untuk mendekrip pesan dari task yang sudah diberikan
```sh
echo "U2FsdGVkX199jgh5oANElFdtCxIEvdEvciLi+v+5loE+VCuy6Ii0b+5byb5DXp32RPmT02Ek1pf55ctQN+DHbwCPiVRfFQamDmbHBUpD7as=" | openssl enc -aes-256-cbc -d -a -kfile default_secret
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/crypto%20basics/crypto%20basic%2020.JPG)

- **Pertanyaan:** What is the unencrypted message
- **Jawaban:**
 ```sh
Leaving passwords in docker images is not so secure
```
- **Pertanyaan:** and what is the name of the file that stored the password
- **Jawaban:**
```sh
default_secret
```