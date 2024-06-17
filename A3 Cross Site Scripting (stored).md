# Cross Site Scripting (stored)
- Masukkan payload XSS berikut ini ke field **comment** lalu post komentar tersebut
```sh
<script>webgoat.customjs.phoneHome()</script>
```

- Setelah komentar berhasil diposting, klik kanan komentar lalu pilih **Inspect**


- Setelah itu pindah ke tab **Console**, disini kita mendapatkan hasil dari payload diatas. Di response tersebut terdapat informasi `phoneHome` untuk menjawab pertanyaan


- **Pertanyaan:** Watching in your browser’s developer tools or your proxy, the output should include a value starting with 'phoneHome Response is …​." Put that value below to complete this exercise. Note that each subsequent call to the phoneHome method will change that value. You may need to ensure you have the most recent one.
- **Jawaban:**
```sh
252303725
```