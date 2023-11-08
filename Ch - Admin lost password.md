# Admin lost password
-  Jalankan tool Burp Suite dan pastikan intercept dalam kondisi On

- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/Challenge1.lesson/1 dan reload

- Setelah Burp Suite terbuka tekan tombol **Forward** berulang kali hingga menemukan request yang mengarah ke path URL **/WebGoat/challenge/logo**


- Klik kanan dan pilih **Send to Repeater**

- Matikan intercept

- Pindah ke tab Repeater dan tekan tombol **Send** dan telusuri hasil response

- Pada response terdapat informasi username dan password sebagai berikut
```sh
admin:!!webgoat_admin_8384!!
```

- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/Challenge1.lesson/1 dan masukkan password admin diatas dan tekan tombol **Sign In**

- Setelah login berhasil kita akan mendapatkan flag. Masukkan flag tersebut di field flag dan tekan tombol **Submit**

