# Cross-Site Request Forgeries
CSRF atau XSRF adalah jenis eksploitasi berbahaya pada situs web di mana perintah tidak sah dikirimkan dari pengguna yang mengunjungi situs web tersebut.

## Basic Get CSRF Exercise
- Buka halaman http://127.0.0.1:9001/WebGoat/start.mvc#lesson/CSRF.lesson/2
- Klik kanan pada samping tombol **Submit Query** lalu pilih Inspect
- Temukan sebuah form di sekitar tombol tersebut

- Sekarang kita copy form tersebut dengan cara klik kanan lalu pilih Copy > Outer HTML


- Disini webgoat berjalan di localhost dan port 9001 sehingga kita perlu menambahkan informasi tersebut pada atribut action sehingga source code nya menjadi seperti berikut ini, simpan dengan nama **csrf.html**
```sh
<form accept-charset="UNKNOWN" id="basic-csrf-get" method="POST" name="form1" target="_blank" successcallback="" action="http://127.0.0.1:9001/WebGoat/csrf/basic-get-flag">
	<input name="csrf" type="hidden" value="false">
	<input type="submit" name="submit">
</form>
```
- Login ke web wolf di tab baru melalui url http://127.0.0.1:9090/login dan login menggunakan akun yang anda gunakan di webgoat

- Pergi ke menu Files

- Unggah file **csrf.html**

- Jika sudah berhasil terunggah klik link

- Lalu tekan tombol **Submit Query**

- Kembali ke halaman webgoat dan masukkan nilai flag