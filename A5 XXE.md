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