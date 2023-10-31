# Server-Side Request Forgery
Dalam serangan Server-Side Request Forgery (SSRF), penyerang dapat menyalahgunakan fungsionalitas di server untuk membaca atau memperbarui sumber daya internal. Penyerang dapat memodifikasi URL tempat kode berjalan dan server akan membacanya dan mengirimkan data. Selain itu, dengan memilih URL secara hati-hati, penyerang dapat membaca konfigurasi server seperti metadata AWS, terhubung ke layanan internal seperti database, atau melakukan permintaan posting terhadap layanan internal yang tidak dimaksudkan untuk diekspos.

## Find and modify the request to display Jerry
- Tekan tombol **Steal the Cheese**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%201.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%202.JPG)

- Klik kanan pada tombol **Steal the Cheese** lalu pilih Inspect

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%203.JPG)

- Sebelum element tombol, terdapat satu buah kolom yang berisi 1 buah input bertipe hidden

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%204.JPG)

- Sekarang kita ubah value pada input tersebut. Klik kanan pada input tersebut lalu pilih Attributes > Edit Attribute "value"

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%205.JPG)

- Ubah dari **tom.png** menjadi **jerry.png** jika sudah tekan tombol close
```sh
images/jerry.png
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%206.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%207.JPG)

-  Tekan tombol **Steal the Cheese** sekali lagi, maka kita berhasil mendapatkan foto jerry

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%208.JPG)

## Change the request, so the server gets information from http://ifconfig.pro
- Klik kanan pada tombol **try this** lalu pilih Inspect

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%209.JPG)

- Sebelum element tombol, terdapat satu buah kolom yang berisi 1 buah input bertipe hidden

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%2010.JPG)

- Sekarang kita ubah value pada input tersebut. Klik kanan pada input tersebut lalu pilih Attributes > Edit Attribute "value"

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%2011.JPG)

- Ubah dari **images/cat.png** menjadi **http://ifconfig.pro** jika sudah tekan tombol close
```sh
http://ifconfig.pro
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%2012.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%2013.JPG)

- Klik tombol **try this** dan tunggu beberapa saat

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%2014.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Server-side%20request%20forgery/ssrf%2015.JPG)