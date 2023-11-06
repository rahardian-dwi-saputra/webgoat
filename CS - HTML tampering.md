# HTML tampering
Browser umumnya menawarkan banyak pilihan untuk mengedit konten yang ditampilkan. Oleh karena itu, Developer harus menyadari bahwa nilai yang dikirim oleh pengguna mungkin telah diubah.

## Try it yourself
- Jalankan tool Burp Suite
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/HtmlTampering.lesson/1 dan tekan tombol **Checkout**

- Cari request yang mengarah ke path URL **/WebGoat/HtmlTampering/task** lalu klik kanan pada request tersebut lalu pilih Send to Repeater

- Pindah ke tab Repeater

- Ubah total harga menjadi `0`

- Jika sudah tekan tombol **Send**

