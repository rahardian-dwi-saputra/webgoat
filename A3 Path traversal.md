# Path traversal
Path traversal (direktori) adalah kerentanan di mana penyerang dapat mengakses file dan direktori di luar lokasi aplikasi. Hal ini dapat menyebabkan pembacaan file dari direktori lain dan menimpa file sistem penting jika ada file yang diunggah.

## Path traversal while uploading files
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/PathTraversal.lesson/1 Klik icon foto kemudian masukkan foto profil

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%201.JPG)

- Tambahkan tanda `../` pada field fullname lalu tekan tombol **Update**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%202.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%203.JPG)

## Path traversal while uploading files
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/PathTraversal.lesson/2 Klik icon foto kemudian masukkan foto profil

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%204.JPG)

- Tambahkan tanda `....//` pada field fullname lalu tekan tombol **Update**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%205.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%206.JPG)

## Path traversal while uploading files
- Pengembang kembali menyadari kerentanan tersebut dengan tidak memvalidasi input kolom input nama lengkap. Perbaikan telah diterapkan dalam upaya mengatasi kerentanan ini. Sekali lagi tugas yang sama, tetapi bisakah Anda melewati perbaikan yang diterapkan?
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/PathTraversal.lesson/3 Klik icon foto kemudian masukkan foto profil

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%207.JPG)

- Jalankan tool Burp Suite dan pastikan Intercept dalam kondisi On

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%208.JPG)

- Tekan tombol **Update**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%209.JPG)

- Setelah Burp Suite terbuka pastikan request mengarah ke path URL **/WebGoat/PathTraversal/profile-upload-remove-user-input**. Jika belum anda dapat menekan tombol Forward beberapa kali hingga menemukan request tersebut

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2010.JPG)

- Tambahkan tanda `../` di filename kemudian tekan tombol **Forward**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2011.JPG)

- Matikan intercept

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2012.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2013.JPG)

- Buka kembali halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/PathTraversal.lesson/3

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2014.JPG)

## Retrieving other files with a path traversal
- Jalankan tool Burp Suite
- Klik tombol **Show random cat picture**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2015.JPG)

- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/PathTraversal/random-picture**. Klik kanan di request tersebut lalu pilih Send to Repeater

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2016.JPG)

- Pindah ke tab Repeater dan klik tombol **Send**. Di response ditemukan parameter **id=8.jpg**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2017.JPG)

- Kita akan ganti nilai id dengan `../../` tapi sebelum itu kita perlu meng-encode nilai tersebut menjadi URL. Buka tab decoder Burp Suite dan ketikkan `../../`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2018.JPG)

- Pilih Encode as .. > URL

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2019.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2020.JPG)

- Copy hasil encode diatas, kemudian pindah ke tab Repeater. Tambahkan parameter id di URL request seperti berikut
```sh
?id=%2e%2e%2f%2e%2e%2f
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2021.JPG)

- Jika sudah tekan tombol **Send**. Di response kita berhasil menemukan lokasi direktori dimana file gambar tersebut berada

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2022.JPG)

- Jadi untuk menemukan file `path-traversal-secret.jpg` cukup tambahkan nilai berikut di parameter id kemudian tekan tombol **Send**
```sh
?id=%2e%2e%2f%2e%2e%2fpath-traversal-secret
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2023.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2024.JPG)

- Buka terminal dan ubah username anda menjadi hash sha256 dengan perintah berikut
```sh
echo -n 'usernameanda' | sha512sum
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2025.JPG)

- Copy hash diatas lalu paste di field flag untuk menjawab soal

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2026.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/path%20traversal/path%20traversal%2027.JPG)