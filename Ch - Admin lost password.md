# Admin lost password
-  Jalankan tool Burp Suite dan pastikan intercept dalam kondisi On

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%201.JPG)

- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/Challenge1.lesson/1 dan reload
- Setelah Burp Suite terbuka tekan tombol **Forward** berulang kali hingga menemukan request yang mengarah ke path URL **/WebGoat/challenge/logo**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%202.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%203.JPG)

- Klik kanan dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%204.JPG)

- Matikan intercept

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%205.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%206.JPG)

- Pindah ke tab Repeater dan tekan tombol **Send** dan telusuri hasil response

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%207.JPG)

- Pada response terdapat informasi username dan password sebagai berikut
```sh
admin:!!webgoat_admin_8384!!
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%208.JPG)

- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/Challenge1.lesson/1 dan masukkan password admin diatas dan tekan tombol **Sign In**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%209.JPG)

- Setelah login berhasil kita akan mendapatkan flag. Masukkan flag tersebut di field flag dan tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%2010.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%2011.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/admin%20lost%20password/lost%20password%2012.JPG)