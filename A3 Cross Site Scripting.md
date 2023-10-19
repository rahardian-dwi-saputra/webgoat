# Cross Site Scripting
Cross Site Scripting (juga dikenal sebagai XSS) adalah kerentanan/cacat yang menggabungkan pemberian tag HTML/skrip sebagai masukan yang ditampilkan ke dalam browser tanpa pengkodean atau sanitasi.

## Try It! Using Chrome or Firefox
- Centang checkbox lalu tekan tombol **Submit**

## Try It! Reflected XSS
- Masukkan script berikut pada field credit card number lalu tekan tombol **Purchace**
```sh
<script>alert(1);</script>
```