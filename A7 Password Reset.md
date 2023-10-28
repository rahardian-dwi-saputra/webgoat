# Password reset
Masing-masing dari kita pasti pernah menggunakan fungsi pengaturan ulang kata sandi di sebuah situs web. Setiap situs web mengimplementasikan fungsi ini dengan cara yang berbeda. Ada yang mengharuskan menjawab beberapa pertanyaan keamanan dan ada juga yang
mengirim link via email. Di pelajaran kali ini kita akan membahas beberapa fungsi pengaturan ulang kata sandi dan menunjukkan dimana letak kesalahannya.

## Email functionality with WebWolf
- Buka website webwolf di tab baru http://127.0.0.1:9090/login dan login dengan username dan password yang digunakan untuk login di webgoat

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%201.JPG)

- Sekarang kembali ke tab halaman website webgoat http://127.0.0.1:9001/WebGoat/start.mvc#lesson/PasswordReset.lesson/1 lalu klik link **Forgot your password?**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%202.JPG)

- Isi email dengan format `username@webgoat.org` lalu tekan tombol **Continue**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%203.JPG)

- Pindah ke tab halaman website webwolf dan pergi ke menu **Mailbox**, jika belum ada email masuk silahkan tekan tombol reload

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%204.JPG)

- Buka email tersebut untuk mengetahui password yang baru

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%205.JPG)

- Pindah ke tab halaman website webgoat, lalu klik link **Account Access**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%206.JPG)

- Isi email dengan format `username@webgoat.org` dan masukkan password yang diterima di menu **Mailbox** website webwolf kemudian tekan tombol **Access**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%207.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%208.JPG)

## Security questions
- Ini terjadi ketika anda kehilangan kata sandi, situs web akan menanyakan pertanyaan keamanan yang Anda jawab saat proses registerasi. Seringkali pertanyaan keamanan memiliki jawaban yang terbatas. Untuk meningkatkan keamanan fungsi ini, pengguna harus dapat memilih pertanyaan sendiri dan mengetikkan jawabannya juga sehingga dapat mempersulit penyerang untuk menebaknya. Pertanyaan keamanan yang bagus bisa dilihat di http://goodsecurityquestions.com/ 
- Kali ini kita akan memdemokan contoh celah keamanan dari security questions, pertama-tama jalankan tool Burp Suite terlebih dahulu
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/PasswordReset.lesson/3 isi username dengan **webgoat** dan jawaban pertanyaan **red** sesuai petunjuk soal

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%209.JPG)

- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/PasswordReset/questions** lalu klik kanan dan pilih **Send to Intruder**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%2010.JPG)

- Pindah ke Tab Intruder

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%2011.JPG)

- Ubah Attack type menjadi Cluster bomb dan bersihkan tanda payload dengan tombol **Clear §**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%2012.JPG)

- Blok value username lalu tekan tombol **Add §** untuk menambahkan penanda payload

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%2013.JPG)

- Blok value securityQuestion lalu tekan tombol **Add §** untuk menambahkan penanda payload

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%2014.JPG)

- Pindah ke Tab Intruder > Payloads, isi payload 1 dengan daftar username. Anda bisa mencopy list user di file [payload security questions.txt](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/payload%20security%20questions.txt) terlebih dahulu lalu tekan tombol Paste

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%2015.JPG)

- Sekarang kita isi payload 2 dengan daftar nama warna. Copy list warna di file [payload security questions.txt](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/payload%20security%20questions.txt) terlebih dahulu lalu tekan tombol Paste. Jika sudah tekan tombol **Start attack** dan tunggu hingga proses penyerangan selesai

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%2016.JPG)

- Sekarang kita cari request yang memiliki panjang paling berbeda diantara request yang lain. Disini kita menemukan 3 kombinasi yang valid. Username larry ternyata memiliki warna favorit yellow

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%2017.JPG)

- Username admin memiliki warna favorit green

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%2018.JPG)

- Dan terakhir username tom memiliki warna favorit purple

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/password%20reset/password%20reset%2019.JPG)