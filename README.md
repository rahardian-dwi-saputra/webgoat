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

## Disclaimer
Semua materi yang disajikan disini hanya digunakan sebagai media pembelajaran. Penulis tidak bertanggung jawab atas penyalahgunaan dari materi tersebut