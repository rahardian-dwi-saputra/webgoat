# Cross Site Scripting
Cross Site Scripting (juga dikenal sebagai XSS) adalah kerentanan/cacat yang menggabungkan pemberian tag HTML/skrip sebagai masukan yang ditampilkan ke dalam browser tanpa pengkodean atau sanitasi.

## Try It! Using Chrome or Firefox
- Centang checkbox lalu tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%201.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%202.JPG)

## Try It! Reflected XSS
- Masukkan script berikut pada field credit card number lalu tekan tombol **Purchace**
```sh
<script>alert(1);</script>
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%203.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%204.JPG)