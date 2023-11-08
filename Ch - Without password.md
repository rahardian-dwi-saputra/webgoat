# Without password
- Jalankan tool Burp Suite
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/Challenge5.lesson dan isi username `Larry` dan masukkan sembarang password

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20password/without%20password%201.JPG)

- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/challenge/5** lalu klik kanan dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20password/without%20password%202.JPG)

- Pindah ke tab Repeater lalu klik tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20password/without%20password%203.JPG)

- Jika kita tambahkan tanda petik di akhir password dan tekan tombol **Send** maka terdapat keterangan SQL error yang menandakan bahwa form login tersebut rentan terhadap SQL injection

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20password/without%20password%204.JPG)

- Lakukan SQL injection dengan menginput password sebagai berikut
```sh
qwerty'+or+'1'%3d'1
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20password/without%20password%205.JPG)

- Jika sudah tekan tombol **Send** maka kita berhasil login tanpa harus mengetahui password aslinya. Copy flag di bagian response

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20password/without%20password%206.JPG)

- Masukkan flag di field flag dan tekan tombol **Submit flag**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20password/without%20password%207.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/without%20password/without%20password%208.JPG)