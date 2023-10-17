# Missing Function Level Access Control
## Relying on obscurity
- Klik kanan pada bagian menu lalu pilih **Inspect**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%201.JPG)

- Disini ditemukan beberapa menu yang sengaja disembunyikan (di hidden)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%202.JPG)

- **Pertanyaan:** Find two invisible menu items in the menu below that are or would be of interest to an attacker/malicious user and submit the labels for those menu items (there are no links right now in the menus).

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%203.JPG)

- **Jawaban**
```sh
Users
Config
```

## Try it
- Jalankan tool Burp Suite. Lalu tekan tombol **Submit** pada halaman berikut ini

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%204.JPG)

- Cari request yang mengarah ke path URL **/WebGoat/access-control/user-hash** lalu klik kanan pada request tersebut lalu pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%205.JPG)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%206.JPG)

- Ubah request dari **POST /WebGoat/access-control/user-hash** menjadi **GET /WebGoat/access-control/users**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%207.JPG)

- Ubah Content-Type dari **application/x-www-form-urlencoded** menjadi **application/json**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%208.JPG)

- Jika sudah tekan tombol **Send** maka akan tampil hash dari user Jerry. Copy hash tersebut untuk menjawab pertanyaan

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%209.JPG)

- **Pertanyaan:** Start with the information you already gathered (hidden menu items) to see if you can pull the list of users and then provide the 'hash' for Jerry’s account.
- Paste hash user Jerry pada field yang sudah disediakan lalu tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2010.JPG)

- **Jawaban**
```sh
SVtOlaa+ER+w2eoIIVE5/77umvhcsh5V8UyDLUa1Itg=
```