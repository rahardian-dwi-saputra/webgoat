# Without password
- Jalankan tool Burp Suite
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/Challenge8.lesson dan tekan salah satu tombol bintang

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20account/without%20account%201.JPG)

- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/challenge/8/vote/** lalu klik kanan dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20account/without%20account%202.JPG)

- Pindah ke tab Repeater lalu klik tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20account/without%20account%203.JPG)

- Ganti `GET` menjadi `HEAD`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20account/without%20account%204.JPG)

- Jika sudah tekan tombol **Send** maka kita berhasil melakukan voting tanpa harus login. Copy flag di bagian response

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20account/without%20account%205.JPG)

- Masukkan flag di field flag dan tekan tombol **Submit flag**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20account/without%20account%206.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20account/without%20account%207.JPG)