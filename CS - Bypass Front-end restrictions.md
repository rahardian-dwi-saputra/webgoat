# Bypass front-end restrictions
Pengguna memiliki kendali yang besar terhadap front-end aplikasi web. Mereka dapat mengubah kode HTML, terkadang juga skrip. Aplikasi yang memerlukan format masukan tertentu juga harus divalidasi di sisi server.

## Field Restrictions
- Jalankan tool Burp Suite
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/BypassRestrictions.lesson/1 dan tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/bypass%20restriction/bypass%20restriction%201.JPG)

- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/BypassRestrictions/FieldRestrictions** lalu klik kanan pada request tersebut dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/bypass%20restriction/bypass%20restriction%202.JPG)

- Pindah ke tab Repeater lalu tekan tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/bypass%20restriction/bypass%20restriction%203.JPG)

- Ubah nilai di masing-masing parameter, disini anda bisa mengubahnya menjadi apapun yang anda mau

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/bypass%20restriction/bypass%20restriction%204.JPG)

- Jika sudah tekan tombol **Send** maka kita berhasil melakukan bypass restriction

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/bypass%20restriction/bypass%20restriction%205.JPG)

## Validation
- Jalankan tool Burp Suite
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/BypassRestrictions.lesson/2 dan tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/bypass%20restriction/bypass%20restriction%206.JPG)

- Buka Burp Suite dan cari request yang mengarah ke path URL **/WebGoat/BypassRestrictions/frontendValidation/** lalu klik kanan pada request tersebut dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/bypass%20restriction/bypass%20restriction%207.JPG)

- Pindah ke tab Repeater lalu tekan tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/bypass%20restriction/bypass%20restriction%208.JPG)

- Sekarang kita ubah nilai di masing-masing field dengan menyimpan rule di masing-masing field, dengan aturan sebagai berikut 
	- Field1 hanya diperbolehkan input huruf kecil kita ubah jadi huruf kapital
	- Field2 hanya diperbolehkan input 3 digit angka kita ubah jadi lebih dari 3 digit angka
	- Field3 hanya diperbolehkan input huruf kecil dan kapital, angka dan spasi kita ubah dengan memasukkan karakter spesial seperti `$,!`
	- Field4 hanya diperbolehkan input sesuai list, kita inputkan digit angka yang diluar list
	- Field5 hanya diperbolehkan input angka kita ubah jadi input alphabet
	- Field6 hanya diperbolehkan input angka dan tanda `-` kita ubah jadi input alphabet
	- Field7 hanya diperbolehkan input nomor telepon kita ubah jadi input angka random

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/bypass%20restriction/bypass%20restriction%209.JPG)

- Jika sudah tekan tombol **Send** maka kita berhasil melakukan bypass restriction terhadap validasi form

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/bypass%20restriction/bypass%20restriction%2010.JPG)