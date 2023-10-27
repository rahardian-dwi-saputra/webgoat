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