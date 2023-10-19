# Cross Site Scripting
Cross Site Scripting (juga dikenal sebagai XSS) adalah kerentanan/cacat yang menggabungkan pemberian tag HTML/skrip sebagai masukan yang ditampilkan ke dalam browser tanpa pengkodean atau sanitasi.

## Try It! Using Chrome or Firefox
- Centang checkbox lalu tekan tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%201.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%202.JPG)

## Try It! Reflected XSS
- Masukkan script berikut pada field credit card number lalu tekan tombol **Purchace**
```sh
<script>alert(1);</script>
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%203.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%204.JPG)

## Identify potential for DOM-Based XSS
- Klik kanan halaman website lalu pilih **Inspect**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%205.JPG)

- Pindah ke tab **Debugger** lalu klik folder **WebGoat/js** kemudian pilih folder **goatApp**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%206.JPG)

- Setelah itu buka folder **view**, didalam folder view terdapat file **GoatRouter.js**. Klik file tersebut untuk membukanya

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%207.JPG)

- Di file **GoatRouter.js** kita menemukan route URL dimana nilai parameter nya akan digunakan kembali oleh javascript

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%208.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%209.JPG) 

- **Pertanyaan:** So, what is the route for the test code that stayed in the app during production? To answer this question, you have to check the JavaScript source.
- **Jawaban:**
```sh
start.mvc#test/
```

## Try It! DOM-Based XSS
- Buka URL berikut di tab baru
```sh
http://127.0.0.1:9001/WebGoat/start.mvc#test/<script>webgoat.customjs.phoneHome();<%2fscript>
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%2010.JPG)

- Klik kanan halaman website lalu pilih **Inspect**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%2011.JPG)

- Pindah ke tab **Console** untuk menemukan jawaban dari soal

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%2012.JPG)

- **Pertanyaan:** Once you trigger it, a subsequent response will come to your browser’s console with a random number. Put that random number below.

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%2013.JPG)

- **Jawaban:**
```sh
1431180718
```

## Question

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%2014.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%2015.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/cross%20site%20scripting/cross%20site%20scripting%2016.JPG)