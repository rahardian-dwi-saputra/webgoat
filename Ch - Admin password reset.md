# Admin password reset
- Isi form dengan email sesuai dengan username yang anda gunakan di webgoat. Format email: `<username>@webgoat.org`. Jika sudah klik tombol **Reset Password**




- Buka WebWolf di tab baru `http://IP_Server:9090/WebWolf/login`. Login sesuai akun yang anda gunakan di WebGoat

- Jika sudah berhasil login, pergi ke menu **Mailbox**. Jika anda menginputkan email dengan benar akan mendapatkan email reset password seperti berikut ini

- Klik email tersebut untuk membuka isi email. Di dalam email tersebut terdapat link untuk mereset password, klik link tersebut untuk membuka isinya


- Setelah dibuka link tersebut bukan link untuk mereset password admin


- Dari hasil diatas dapat kita ketahui bahwa link untuk mereset password memiliki format URL `http://IP_Server:8080/WebGoat/challenge/7/reset-password/hash`. Jadi kita bisa mereset password admin jika kita mengetahui hash yang digunakan admin. Kita bisa mencari hash tersebut di source code aplikasi WebGoat yang tersedia di github
- Setelah kita melakukan penelusuran source code WebGoat di github. Kita berhasil menemukan hash admin di file `Assignment7.java` di link https://github.com/WebGoat/WebGoat/blob/main/src/main/java/org/owasp/webgoat/lessons/challenges/challenge7/Assignment7.java
```sh
375afe1104f4a487a73823c50a9292a2
```

- Sekarang kita bisa memasukkan hash tersebut pada link reset password. Setelah dimasukkan ke dalam link kita berhasil mendapatkan flag
```sh
1bfa914d-e7bd-48d9-a2e2-89e1bb4c85ba
```

- Input flag tersebut pada field flag untuk menyelesaikan challenge

