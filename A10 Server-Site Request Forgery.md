# Server-Side Request Forgery
Dalam serangan Server-Side Request Forgery (SSRF), penyerang dapat menyalahgunakan fungsionalitas di server untuk membaca atau memperbarui sumber daya internal. Penyerang dapat memodifikasi URL tempat kode berjalan dan server akan membacanya dan mengirimkan data. Selain itu, dengan memilih URL secara hati-hati, penyerang dapat membaca konfigurasi server seperti metadata AWS, terhubung ke layanan internal seperti database, atau melakukan permintaan posting terhadap layanan internal yang tidak dimaksudkan untuk diekspos.

## Find and modify the request to display Jerry
- Tekan tombol **Steal the Cheese**

- Klik kanan pada tombol **Steal the Cheese** lalu pilih Inspect

- Sebelum element tombol, terdapat satu buah kolom yang berisi 1 buah input bertipe hidden

- Sekarang kita ubah value pada input tersebut. Klik kanan pada input tersebut lalu pilih Attributes > Edit Attribute "value"


- Ubah dari **tom.png** menjadi **jerry.png** jika sudah tekan tombol close
```sh
images/jerry.png
```


-  Tekan tombol **Steal the Cheese** sekali lagi, maka kita berhasil mendapatkan foto jerry

## Change the request, so the server gets information from http://ifconfig.pro
- Klik kanan pada tombol **try this** lalu pilih Inspect

- Sebelum element tombol, terdapat satu buah kolom yang berisi 1 buah input bertipe hidden

- Sekarang kita ubah value pada input tersebut. Klik kanan pada input tersebut lalu pilih Attributes > Edit Attribute "value"

- Ubah dari **images/cat.png** menjadi **http://ifconfig.pro** jika sudah tekan tombol close
```sh
http://ifconfig.pro
```

- Klik tombol **try this** dan tunggu beberapa saat