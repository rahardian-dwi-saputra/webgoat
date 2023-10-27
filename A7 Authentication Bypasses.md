# Authentication Bypasses
Authentication Bypass terjadi dalam banyak cara tetapi biasanya memanfaatkan beberapa kelemahan logika untuk mencapai kondisi yang tepat.
- Referensi: https://henryhoggard.co.uk/blog/Paypal-2FA-Bypass

## 2FA Password Reset
- Jalankan tool Burp Suite
- Isi pertanyaan autentikasi dengan sembarang jawaban lalu tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/authentication%20bypass/authentication%20bypass%201.JPG)

- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/auth-bypass/verify-account** lalu klik kanan pada request tersebut dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/authentication%20bypass/authentication%20bypass%202.JPG)

- Pindah ke tab Repeater lalu tekan tombol **Send**, disini terdapat respon `not quite`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/authentication%20bypass/authentication%20bypass%203.JPG)

- Sekarang kita lihat source code di https://github.com/WebGoat/WebGoat/blob/develop/src/main/java/org/owasp/webgoat/lessons/authbypass/AccountVerificationHelper.java disini terlihat jelas bahwa asal nama parameter mengandung kata **secQuestion0** dan **secQuestion1** namun jawabannya tidak tepat, verifikasi tetap dianggap `true`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/authentication%20bypass/authentication%20bypass%204.JPG)

- Buka kembali tab Repeater Burp Suite, sekarang kita cukup ubah nama parameternya menjadi seperti ini

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/authentication%20bypass/authentication%20bypass%205.JPG)

- Jika sudah tekan tombol **Send** maka kita berhasil melakukan bypass autentikasi dengan memanfaatkan kesalahan logika pemrograman

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/authentication%20bypass/authentication%20bypass%206.JPG)