# Insecure Login
Enkripsi adalah alat penting untuk menjaga komunikasi yang aman. Dalam pelajaran ini, kita akan mengetahui mengapa enkripsi harus selalu digunakan saat mengirim data sensitif.

## Let’s try
- Jalankan tool Burp Suite terlebih dahulu, dan pastikan Intercept dalam kondisi On

- Tekan tombol **Log in**

- Setelah request di intercept, terlihat jelas bahwa disini terdapat informasi username dan password untuk login
```sh
{"username":"CaptainJack","password":"BlackPearl"}
```

- Tekan tombol **Forward**

- Setelah itu matikan Intercept

- Sekarang kita masukkan username dan password diatas dan tekan tombol **Submit**

