# Insecure Login
Enkripsi adalah alat penting untuk menjaga komunikasi yang aman. Dalam pelajaran ini, kita akan mengetahui mengapa enkripsi harus selalu digunakan saat mengirim data sensitif.

## Let’s try
- Jalankan tool Burp Suite terlebih dahulu, dan pastikan Intercept dalam kondisi On

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/insecure%20login/insecure%20login%201.JPG)

- Tekan tombol **Log in**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/insecure%20login/insecure%20login%202.JPG)

- Setelah request di intercept, terlihat jelas bahwa disini terdapat informasi username dan password untuk login
```sh
{"username":"CaptainJack","password":"BlackPearl"}
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/insecure%20login/insecure%20login%203.JPG)

- Tekan tombol **Forward**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/insecure%20login/insecure%20login%204.JPG)

- Setelah itu matikan Intercept

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/insecure%20login/insecure%20login%205.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/insecure%20login/insecure%20login%206.JPG)

- Sekarang kita masukkan username dan password diatas dan tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/insecure%20login/insecure%20login%207.JPG)