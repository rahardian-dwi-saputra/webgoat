# Without password
- Jalankan tool Burp Suite
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/Challenge8.lesson dan tekan salah satu tombol bintang



- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/challenge/5** lalu klik kanan dan pilih **Send to Repeater**


- Pindah ke tab Repeater lalu klik tombol **Send**


- Ganti `GET` menjadi `HEAD`

- Jika sudah tekan tombol **Send** maka kita berhasil melakukan voting tanpa harus login. Copy flag di bagian response



- Masukkan flag di field flag dan tekan tombol **Submit flag**
