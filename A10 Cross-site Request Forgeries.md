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