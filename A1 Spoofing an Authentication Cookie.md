# Spoofing an Authentication Cookie
- Jalankan tool Burp Suite terlebih dahulu
- Masukkan username `webgoat` dan password `webgoat` lalu tekan tekan tombol **Access**

- Buka Burp Suite lalu cari request yang mengarah ke path URL **/WebGoat/SpoofCookie/login** lalu klik kanan pada request tersebut dan pilih **Send to Repeater**

- Pindah ke tab Repeater lalu klik tombol **Send**. Pada field response kita mendapat cookie **spoof_auth**. Copy isi cookie tersebut

- Buka tool Cyber Chef https://gchq.github.io/CyberChef/ lalu tarik menu **From Base64** ke field **Recipe**


- Paste nilai **spoof_auth** ke field **Input**. Setelah didecode menggunakan base64 hasilnya masih berupa bilangan hexa sehingga kita perlu melakukan decode lagi dari bilangan hexa ke sebuah string yang mudah dibaca. Tarik menu **From Hex** ke field **Recipe**

- Setelah didecode ke string hasilnya berupa string terbalik sehingga kita perlu balik string tersebut supaya mudah dibaca. Pada field pencarian ketik `reverse` lalu tarik menu **Reverse** ke field recipe

- Setelah melewati beberapa proses decode kita tahu bahwa username `webgoat` akan meng -generate cookie **spoof_auth** yang berisi string `webgoatcvEOHBlhHc`


- Sekarang kita kembali ke tab Repeater Burp Suite. Ubah username menjadi `admin` dan password menjadi `admin`

- Lalu tekan tombol **Send**. Pada field response kita mendapat cookie **spoof_auth** dari user admin. Copy isi cookie tersebut

- Paste nilai cookie tersebut ke field **Input** Cyber Chef. Dengan proses decode yang sama, user admin akan meng-generate cookie **spoof_auth** yang berisi string `admincvEOHBlhHc`

- Setelah mengetahui polanya. Kita tahu bahwa user `Tom` akan meng-generate cookie **spoof_auth** yang berisi string `tomcvEOHBlhHc`
- Sekarang kita tinggal meng-encode string tersebut supaya bisa di injeksikan ke sistem. Buka kembali tool Cyber Chef https://gchq.github.io/CyberChef/   