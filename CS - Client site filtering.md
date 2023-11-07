# Client side filtering
Merupakan praktik yang baik untuk hanya mengirimkan informasi ke klien yang seharusnya dapat mereka akses. Dalam pelajaran ini, terlalu banyak informasi yang dikirim ke klien, sehingga menimbulkan masalah kontrol akses yang serius. Untuk latihan ini, misi Anda adalah mengeksploitasi informasi asing yang dikembalikan oleh server untuk menemukan informasi yang seharusnya tidak dapat Anda akses.

## Salary manager
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/ClientSideFiltering.lesson/1 lalu pilih user **Larry Stooge**

- Klik kanan pada field select lalu klik **Inspect**

- Temukan elemen tabel tersembunyi lalu buka isi tiap elemen tabel tersebut hingga menemukan informasi salary **Neville Bartholomew**

- Setelah berhasil menemukan input ke field answer lalu tekan tombol **Submit Answer**


## No need to pay if you know the code
- Buka source code webgoat di link https://github.com/WebGoat/WebGoat/blob/main/src/test/java/org/owasp/webgoat/lessons/clientsidefiltering/ShopEndpointTest.java
- Disini terdapat informasi kode kupon yang bisa kita coba

- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/ClientSideFiltering.lesson/2 dan inputkan kode kupon diatas
```sh
get_it_for_free
```

