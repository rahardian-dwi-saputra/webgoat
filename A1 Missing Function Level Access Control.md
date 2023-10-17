# Missing Function Level Access Control
## Relying on obscurity
- Klik kanan pada bagian menu lalu pilih **Inspect**

- Disini ditemukan beberapa menu yang sengaja disembunyikan (di hidden)

- **Pertanyaan:** Find two invisible menu items in the menu below that are or would be of interest to an attacker/malicious user and submit the labels for those menu items (there are no links right now in the menus).

- **Jawaban**
```sh
Users
Config
```

## Try it
- Jalankan tool Burp Suite. Lalu tekan tombol **Submit** pada halaman berikut ini

- Cari request yang mengarah ke path URL **/WebGoat/access-control/user-hash** lalu klik kanan pada request tersebut lalu pilih **Send to Repeater**

- Pindah ke tab Repeater

- Ubah request dari **POST /WebGoat/access-control/user-hash** menjadi **GET /WebGoat/access-control/users**

- Ubah Content-Type dari **application/x-www-form-urlencoded** menjadi **application/json**

- Jika sudah tekan tombol **Send** maka akan tampil hash dari user Jerry. Copy hash tersebut untuk menjawab pertanyaan

- **Pertanyaan:** Start with the information you already gathered (hidden menu items) to see if you can pull the list of users and then provide the 'hash' for Jerry’s account.
- Paste hash user Jerry pada field yang sudah disediakan lalu tekan tombol **Submit**

- **Jawaban**
```sh
SVtOlaa+ER+w2eoIIVE5/77umvhcsh5V8UyDLUa1Itg=
```