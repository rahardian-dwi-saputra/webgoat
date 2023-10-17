# Insecure Direct Object References

Insecure Direct Object References (IDOR) terjadi ketika aplikasi web melakukan akses langsung ke objek dalam database internal tetapi tidak memeriksa kontrol akses atau otorisasi.

## Authenticate First, Abuse Authorization Later
- Masukkan user `tom` dan pass `cat` sesuai petunjuk soal

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%201.JPG)

## Observing Differences & Behaviors
- Jalankan tool `Burp Suite` terlebih dahulu, kemudian tekan tombol **View Profile**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%202.JPG)

- Setelah request berhasil direkam. Kita mendapati request untuk menampilkan informasi profil. Klik kanan pada request tersebut lalu pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%203.JPG)

- Setelah itu pindah ke tab Repeater dan tekan tombol **Send**. Disini kita mendapati parameter yang tidak ditampilkan di halaman web yaitu parameter role dan userId

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%204.JPG)  

- **Pertanyaan:** In the text input below, list the two attributes that are in the server’s response, but don’t show above in the profile.
-**Jawaban:**
```sh
role, userId
```

## Guessing & Predicting Patterns
- Sebelum request mengarah ke path URL **/WebGoat/IDOR/profile** terdapat sebuah request yang mengarah ke **/WebGoat/service/lessonoverview.mvc**. Di request tersebut terdapat keterangan path URL untuk menampilkan informasi profil user

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%205.JPG)

- **Pertanyaan:** Please input the alternate path to the Url to view your own profile. Please start with 'WebGoat' (i.e. disregard 'http://localhost:8080/')
- Dari task sebelumnya kita memperoleh nilai parameter userId yaitu **2342384**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%206.JPG)

- **Jawaban:**
```sh
WebGoat/IDOR/profile/2342384
``` 

## Playing with the Patterns
- Tekan tombol **View Profile**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%207.JPG)

- Cari request yang mengarah ke path URL **/WebGoat/IDOR/profile/%7BuserId%7D** di Burp Suite. Lalu klik kanan pada request tersebut dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%208.JPG)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%209.JPG)

- Dari pertanyaan sebelumnya kita memperoleh userId **2342384**. Ganti **%7BuserId%7D** menjadi **2342384** lalu tekan tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%2010.JPG)

- Tambahkan nilai 1 pada userId **2342384** secara berkala lalu tekan tombol **Send**. Lakukan berulang kali dengan userId yang berbeda seperti 2342385, 2342386, 2342387 dan seterusnya hingga mendapatkan nama user **Buffalo Bill**. Nama user **Buffalo Bill** berhasil ditemukan pada userId **2342388**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%2011.JPG)

- Sekarang kita edit data profil user **Buffalo Bill**. Pertama-tama ubah method **GET** menjadi **PUT**
```sh
PUT /WebGoat/IDOR/profile/2342388 HTTP/1.1
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%2012.JPG)

- Ubah Content-Type dari `application/x-www-form-urlencoded` menjadi `application/json`
```sh
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%2013.JPG)

- Tambahkan kode berikut pada bagian paling bawah
```sh
Content-Length: 82
{"role":1, "color":"red", "size":"large", "name":"Buffalo Bill", "userId":2342388}
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%2014.JPG)

- Jika sudah tekan tombol **Send**. Jika terjadi error seperti gambar dibawah ini hapus **Content-Length** pada bagian bawah lalu klik tombol **Send** lagi

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%2015.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/IDOR/idor%2016.JPG)