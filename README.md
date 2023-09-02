# OWASP WebGoat
WebGoat adalah aplikasi web rentan (tidak aman) yang memungkinkan pengembang (developer) menguji celah keamanan yang umum ditemukan dalam aplikasi berbasis Java. OWASP WebGoat berisi contoh-contoh OWASP Top 10 vulnerabilities

## Instalasi di Kali Linux
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
- **(A2) Cryptographic Fairules**
	- [Crypto Basics](A2%20Crypto%20Basics.md)
- **(A3) Injection**
	- [SQL Injection (intro)](A3%20SQL%20Injection%20Intro.md)
- **(A5) Security Misconfiguration**
- **(A7) Vuln and Outdated Components**
- **(A8) Identity & Auth Failure**