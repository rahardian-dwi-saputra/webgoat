# Spoofing an Authentication Cookie
- Jalankan tool Burp Suite terlebih dahulu
- Masukkan username `webgoat` dan password `webgoat` lalu tekan tekan tombol **Access**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%201.JPG)

- Buka Burp Suite lalu cari request yang mengarah ke path URL **/WebGoat/SpoofCookie/login** lalu klik kanan pada request tersebut dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%202.JPG)

- Pindah ke tab Repeater lalu klik tombol **Send**. Pada field response kita mendapat cookie **spoof_auth**. Copy isi cookie tersebut

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%203.JPG)

- Buka tool Cyber Chef https://gchq.github.io/CyberChef/ lalu tarik menu **From Base64** ke field **Recipe**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%204.jpg)

- Paste nilai **spoof_auth** ke field **Input**. Setelah didecode menggunakan base64 hasilnya masih berupa bilangan hexa sehingga kita perlu melakukan decode lagi dari bilangan hexa ke sebuah string yang mudah dibaca. Tarik menu **From Hex** ke field **Recipe**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%205.jpg)

- Setelah didecode ke string hasilnya berupa string terbalik sehingga kita perlu balik string tersebut supaya mudah dibaca. Pada field pencarian ketik `reverse` lalu tarik menu **Reverse** ke field recipe

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%206.jpg)

- Setelah melewati beberapa proses decode kita tahu bahwa username `webgoat` akan meng -generate cookie **spoof_auth** yang berisi string `webgoatcvEOHBlhHc`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%207.JPG)

- Sekarang kita kembali ke tab Repeater Burp Suite. Ubah username menjadi `admin` dan password menjadi `admin`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%208.JPG)

- Lalu tekan tombol **Send**. Pada field response kita mendapat cookie **spoof_auth** dari user admin. Copy isi cookie tersebut

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%209.JPG)

- Paste nilai cookie tersebut ke field **Input** Cyber Chef. Dengan proses decode yang sama, user admin akan meng-generate cookie **spoof_auth** yang berisi string `admincvEOHBlhHc`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%2010.JPG)

- Setelah mengetahui polanya. Kita tahu bahwa user `Tom` akan meng-generate cookie **spoof_auth** yang berisi string `tomcvEOHBlhHc`
- Sekarang kita tinggal meng-encode string tersebut supaya bisa di injeksikan ke sistem. Buka kembali tool Cyber Chef https://gchq.github.io/CyberChef/ dan masukkan string `tomcvEOHBlhHc` pada field Input

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%2011.JPG)

- Pada field pencarian ketik `reverse` lalu tarik menu **Reverse** ke field recipe

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%2012.jpg)

- Pada field pencarian ketik `hex` lalu tarik menu **To Hex** ke field recipe

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%2013.jpg)

- Ubah Delimiter **To Hex** menjadi **None**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%2014.JPG)

- Pada field pencarian ketik `base64` lalu tarik menu **To Base64** ke field recipe

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%2015.jpg)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%2016.JPG)

- Kini kita telah berhasil meng-encode cookie user `Tom`. Sekarang kita tinggal menginjekkan cookie tersebuat dengan bantuan tool Burp Suite. Buka tab Repeater kembali lalu lakukan modifikasi cookie dan tekan tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%2017.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/spoofing%20an%20authentication%20cookie/spoofing%20auth%2018.JPG)