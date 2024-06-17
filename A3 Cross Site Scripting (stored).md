# Cross Site Scripting (stored)
- Masukkan payload XSS berikut ini ke field **comment** lalu post komentar tersebut
```sh
<script>webgoat.customjs.phoneHome()</script>
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting%20stored/xss%20stored%201.JPG)

- Setelah komentar berhasil diposting, klik kanan komentar lalu pilih **Inspect**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting%20stored/xss%20stored%202.JPG)

- Setelah itu pindah ke tab **Console**, disini kita mendapatkan hasil dari payload diatas. Di response tersebut terdapat informasi `phoneHome` untuk menjawab pertanyaan

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting%20stored/xss%20stored%203.JPG)

- **Pertanyaan:** Watching in your browser’s developer tools or your proxy, the output should include a value starting with 'phoneHome Response is …​." Put that value below to complete this exercise. Note that each subsequent call to the phoneHome method will change that value. You may need to ensure you have the most recent one.

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting%20stored/xss%20stored%204.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting%20stored/xss%20stored%205.JPG)

- **Jawaban:**
```sh
252303725
```