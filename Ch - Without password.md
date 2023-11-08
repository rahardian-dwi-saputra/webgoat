# Without password
- Jalankan tool Burp Suite
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/Challenge5.lesson dan isi username `Larry` dan masukkan sembarang password

- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/challenge/5** lalu klik kanan dan pilih **Send to Repeater**


- Pindah ke tab Repeater lalu klik tombol Send

- Jika kita tambahkan tanda petik di akhir password dan tekan tombol **Send** maka terdapat keterangan SQL error yang menandakan bahwa form login tersebut rentan terhadap SQL injection

- Lakukan SQL injection dengan menginput password sebagai berikut
```sh
qwerty'+or+'1'%3d'1
```

- Jika sudah tekan tombol **Send** maka kita berhasil login tanpa harus mengetahui password aslinya. Copy flag di bagian response

- Masukkan flag di field flag dan tekan tombol **Submit flag**

