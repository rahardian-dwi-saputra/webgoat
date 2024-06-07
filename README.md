# OWASP WebGoat
WebGoat adalah aplikasi web rentan (tidak aman) yang memungkinkan pengembang (developer) menguji celah keamanan yang umum ditemukan dalam aplikasi berbasis Java. OWASP WebGoat berisi contoh-contoh OWASP Top 10 vulnerabilities

## Instalasi di Ubuntu menngunakan Docker
- Sebelum menginstall OWASP WebGoat, kita perlu menginstall docker terlebih dahulu
```sh
sudo apt install -y docker.io
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/instalasi/1.JPG)

- Install docker-compose
```sh
sudo apt install docker-compose
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/instalasi/2.JPG)

- Jalankan service docker
```sh
sudo systemctl enable docker --now
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/instalasi/3.JPG)

- Pull docker image webgoat
```sh
sudo docker pull webgoat/webgoat
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/instalasi/4.JPG)

- Jalankan aplikasi WebGoat, disini kita menggunakan IP `0.0.0.0` supaya WebGoat dapat diakses di mesin lainnya seperti Kali Linux dan Time Zone yang kita gunakan adalah `Asia/Jakarta`. Anda bisa mengubahnya sesuai keinginan anda
```sh
sudo docker run -p 0.0.0.0:8080:8080 -p 0.0.0.0:9090:9090 -e TZ=Asia/Jakarta webgoat/webgoat
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/instalasi/5.JPG)

- WebGoat dapat diakses melalui URL `http://<IP_SERVER>:8080/WebGoat`. Setelah berhasil diakses lakukan registerasi terlebih dahulu dengan mengklik link register

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/instalasi/6.JPG)

- Isi sesuai kemauan anda lalu tekan tombol **Sign up**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/instalasi/7.JPG)

- Jika register berhasil, kita akan diarahkan otomatis masuk ke aplikasi WebGoat

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/instalasi/8.JPG)

- Untuk WebWolf bisa diakses melalui URL `http://<IP_SERVER>:9090/WebWolf`. Gunakan username dan password yang sudah diregister diatas untuk Login

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/instalasi/9.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/instalasi/10.JPG)

## Instalasi di Kali Linux menggunakan file JAR
- Download File Jar di https://github.com/WebGoat/WebGoat/releases
- Jalankan OWASP WebGoat di port yang berbeda, misalnya port 9001
```sh
WEBGOAT_PORT=9001 java -jar webgoat-2023.4.jar
```
- Buka browser dan buka URL berikut ini kemudian lakukan registrasi 
```sh
http://127.0.0.1:9001/WebGoat
```

## Lesson
- **(A1) Broken Access Control**
	- [Insecure Direct Object References(IDOR)](A1%20Insecure%20Direct%20Object%20References.md)
	- [Spoofing an Authentication Cookie](A1%20Spoofing%20an%20Authentication%20Cookie.md)
- **(A2) Cryptographic Fairules**
	- [Crypto Basics](A2%20Crypto%20Basics.md)
- **(A3) Injection**
	- [SQL Injection (intro)](A3%20SQL%20Injection%20Intro.md)
	- [SQL Injection (mitigation)](A3%20SQL%20Injection%20mitigation.md)
	- [Path traversal](A3%20Path%20traversal.md)
	- [Cross Site Scripting(XSS)](A3%20Cross%20Site%20Scripting.md)
- **(A5) Security Misconfiguration**
	- [XXE](A5%20XXE.md)
- **(A6) Vuln and Outdated Components**
- **(A7) Identity & Auth Failure**
	- [Authentication Bypasses](A7%20Authentication%20Bypasses.md)
	- [Insecure Login](A7%20Insecure%20Login.md)
	- [JWT tokens](A7%20JWT%20Tokens.md)
	- [Password reset](A7%20Password%20Reset.md)
	- [Secure Passwords](A7%20Secure%20Passwords.md)
- **(A8) Software & Data Integrity**
- **(A9) Security Logging Fairules**
	- [Logging Security](A9%20Logging%20Security.md)
- **(A10) Server-side Request Forgery**
	- [Cross-Site Request Forgeries(CSRF)](A10%20Cross-site%20Request%20Forgeries.md)
	- [Server-Site Request Forgery(SSRF)](A10%20Server-Site%20Request%20Forgery.md)
- Client side
	- [Bypass front-end restrictions](CS%20-%20Bypass%20Front-end%20restrictions.md)
	- [Client side filtering](CS%20-%20Client%20site%20filtering.md)
	- [HTML tampering](CS%20-%20HTML%20tampering.md)
- Challenges
	- [Admin lost password](Ch%20-%20Admin%20lost%20password.md)
	- [Without password](Ch%20-%20Without%20password.md)
	- [Without account](Ch%20-%20Without%20account.md)

## Disclaimer
Semua materi yang disajikan disini hanya digunakan sebagai media pembelajaran. Penulis tidak bertanggung jawab atas penyalahgunaan dari materi tersebut