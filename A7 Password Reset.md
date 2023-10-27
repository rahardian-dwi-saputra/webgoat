# Password reset
Masing-masing dari kita pasti pernah menggunakan fungsi pengaturan ulang kata sandi di sebuah situs web. Setiap situs web mengimplementasikan fungsi ini dengan cara yang berbeda. Ada yang mengharuskan menjawab beberapa pertanyaan keamanan dan ada juga yang
mengirim link via email. Di pelajaran kali ini kita akan membahas beberapa fungsi pengaturan ulang kata sandi dan menunjukkan dimana letak kesalahannya.

## Email functionality with WebWolf
- Buka website webwolf di tab baru http://127.0.0.1:9090/login dan login dengan username dan password yang digunakan untuk login di webgoat

- Sekarang kembali ke tab halaman website webgoat http://127.0.0.1:9001/WebGoat/start.mvc#lesson/PasswordReset.lesson/1 lalu klik link **Forgot your password?**


- Isi email dengan format `username@webgoat.org` lalu tekan tombol **Continue**

- Pindah ke tab halaman website webwolf dan pergi ke menu **Mailbox**, jika belum ada email masuk silahkan tekan tombol reload

- Buka email tersebut untuk mengetahui password yang baru

- Pindah ke tab halaman website webgoat, lalu klik link **Account Access**

- Isi email dengan format `username@webgoat.org` dan masukkan password yang diterima di menu **Mailbox** website webwolf kemudian tekan tombol **Access**

