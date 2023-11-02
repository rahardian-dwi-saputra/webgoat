# Path traversal
Path traversal (direktori) adalah kerentanan di mana penyerang dapat mengakses file dan direktori di luar lokasi aplikasi. Hal ini dapat menyebabkan pembacaan file dari direktori lain dan menimpa file sistem penting jika ada file yang diunggah.

## Path traversal while uploading files
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/PathTraversal.lesson/1 Klik icon foto kemudian masukkan foto profil

- Tambahkan tanda `../` pada field fullname lalu tekan tombol **Update**



## Path traversal while uploading files
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/PathTraversal.lesson/2 Klik icon foto kemudian masukkan foto profil

- Tambahkan tanda `....//` pada field fullname lalu tekan tombol **Update**

## Path traversal while uploading files
- Pengembang kembali menyadari kerentanan tersebut dengan tidak memvalidasi input kolom input nama lengkap. Perbaikan telah diterapkan dalam upaya mengatasi kerentanan ini. Sekali lagi tugas yang sama, tetapi bisakah Anda melewati perbaikan yang diterapkan?
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/PathTraversal.lesson/3 Klik icon foto kemudian masukkan foto profil

- Jalankan tool Burp Suite dan pastikan Intercept dalam kondisi On

- Tekan tombol **Update**

- Setelah Burp Suite terbuka pastikan request mengarah ke path URL **/WebGoat/PathTraversal/profile-upload-remove-user-input**. Jika belum anda dapat menekan tombol Forward beberapa kali hingga menemukan request tersebut


- Tambahkan tanda `../` di filename kemudian tekan tombol **Forward**

- Matikan intercept

- Buka kembali halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/PathTraversal.lesson/3