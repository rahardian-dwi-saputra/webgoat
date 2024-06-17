# Admin password reset
- Isi form dengan email sesuai dengan username yang anda gunakan di webgoat. Format email: `<username>@webgoat.org`. Jika sudah klik tombol **Reset Password**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20password%20reset/reset%20password%201.JPG)

- Buka WebWolf di tab baru `http://IP_Server:9090/WebWolf/login`. Login sesuai akun yang anda gunakan di WebGoat

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20password%20reset/reset%20password%202.JPG)

- Jika sudah berhasil login, pergi ke menu **Mailbox**. Jika anda menginputkan email dengan benar akan mendapatkan email reset password seperti berikut ini

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20password%20reset/reset%20password%203.JPG)

- Klik email tersebut untuk membuka isi email. Di dalam email tersebut terdapat link untuk mereset password, klik link tersebut untuk membuka isinya

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20password%20reset/reset%20password%204.JPG)

- Setelah dibuka link tersebut bukan link untuk mereset password admin

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20password%20reset/reset%20password%205.JPG)

- Dari hasil diatas dapat kita ketahui bahwa link untuk mereset password memiliki format URL `http://IP_Server:8080/WebGoat/challenge/7/reset-password/hash`. Jadi kita bisa mereset password admin jika kita mengetahui hash yang digunakan admin. Kita bisa mencari hash tersebut di source code aplikasi WebGoat yang tersedia di github
- Setelah kita melakukan penelusuran source code WebGoat di github. Kita berhasil menemukan hash admin di file `Assignment7.java` di link https://github.com/WebGoat/WebGoat/blob/main/src/main/java/org/owasp/webgoat/lessons/challenges/challenge7/Assignment7.java
```sh
375afe1104f4a487a73823c50a9292a2
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20password%20reset/reset%20password%206.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20password%20reset/reset%20password%207.JPG)

- Sekarang kita bisa memasukkan hash tersebut pada link reset password. Setelah dimasukkan ke dalam link kita berhasil mendapatkan flag
```sh
1bfa914d-e7bd-48d9-a2e2-89e1bb4c85ba
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20password%20reset/reset%20password%208.JPG)

- Input flag tersebut pada field flag untuk menyelesaikan challenge

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20password%20reset/reset%20password%209.JPG)