# Logging Security
Logging sangat penting untuk sistem modern. Alasannya adalah sebagai berikut:
- Memonitoring aplikasi dan debugging aplikasi
- Audit logging, misalnya mencatat tindakan spesifik user di sistem anda
- Pemantauan Peristiwa Keamanan, misalnya memberikan informasi ke sistem SIEM atau SOAR yang akan terpicu berdasarkan informasi yang diberikan dalam log ini.

## Let’s try
- Masukkan username dan password yang anda gunakan untuk mengakses webgoat

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/logging%20security/logging%20security%201.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/logging%20security/logging%20security%202.JPG)

- Sekarang ubah inputan username menjadi sebagai berikut
```sh
[username]. Login succeeded for username admin.
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/logging%20security/logging%20security%203.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/logging%20security/logging%20security%204.JPG)

## Let’s try
- Untuk menjalankan webgoat kita pasti akan menjalankan perintah ini diterminal
```sh
WEBGOAT_PORT=9001 java -jar webgoat-2023.4.jar
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/logging%20security/logging%20security%205.JPG)

- Saat perintah diatas dijalankan, aplikasi webgoat akan secara otomatis meng-generate password untuk Admin. Anda dapat menelusurinya di log yang muncul diterminal. Copy password tersebut

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/logging%20security/logging%20security%206.JPG)

- Kemudian decode menggunakan base64 di terminal
```sh
echo 'password' | base64 -d
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/logging%20security/logging%20security%207.JPG)

- Masukkan username `Admin` dan password yang sudah di decode diatas di halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/LogSpoofing.lesson/3

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/logging%20security/logging%20security%208.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/logging%20security/logging%20security%209.JPG)