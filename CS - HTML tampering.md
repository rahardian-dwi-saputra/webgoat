# HTML tampering
Browser umumnya menawarkan banyak pilihan untuk mengedit konten yang ditampilkan. Oleh karena itu, Developer harus menyadari bahwa nilai yang dikirim oleh pengguna mungkin telah diubah.

## Try it yourself
- Jalankan tool Burp Suite
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/HtmlTampering.lesson/1 dan tekan tombol **Checkout**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/HTML%20tampering/html%20tampering%201.JPG)

- Cari request yang mengarah ke path URL **/WebGoat/HtmlTampering/task** lalu klik kanan pada request tersebut lalu pilih Send to Repeater

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/HTML%20tampering/html%20tampering%203.JPG)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/HTML%20tampering/html%20tampering%204.JPG)

- Ubah total harga menjadi `0`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/HTML%20tampering/html%20tampering%205.JPG)

- Jika sudah tekan tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/HTML%20tampering/html%20tampering%206.JPG)