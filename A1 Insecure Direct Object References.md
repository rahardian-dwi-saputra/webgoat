# Insecure Direct Object References

## Authenticate First, Abuse Authorization Later
- Masukkan user `tom` dan pass `cat` sesuai petunjuk soal

## Observing Differences & Behaviors
- Jalankan tool `Burp Suite` terlebih dahulu, kemudian tekan tombol **View Profile**

- Setelah request berhasil direkam. Kita mendapati request untuk menampilkan informasi profil. Klik kanan pada request tersebut lalu pilih **Send to Repeater**

- Setelah itu pindah ke tab Repeater dan tekan tombol **Send**. Disini kita mendapati parameter yang tidak ditampilkan di halaman web yaitu parameter role dan userId  

- **Pertanyaan:** In the text input below, list the two attributes that are in the server’s response, but don’t show above in the profile.
-**Jawaban:**
```sh
role, userId
```

## Guessing & Predicting Patterns
- Sebelum request mengarah ke path URL **/WebGoat/IDOR/profile** terdapat sebuah request yang mengarah ke **/WebGoat/service/lessonoverview.mvc**. Di request tersebut terdapat keterangan path URL untuk menampilkan informasi profil user

- **Pertanyaan:** Please input the alternate path to the Url to view your own profile. Please start with 'WebGoat' (i.e. disregard 'http://localhost:8080/')
- Dari task sebelumnya kita memperoleh nilai parameter userId yaitu **2342384** 
- **Jawaban:**
```sh
WebGoat/IDOR/profile/2342384
``` 

## Playing with the Patterns