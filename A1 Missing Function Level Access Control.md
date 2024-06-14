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

- Pada Burp Suite terdapat request yang mengarah ke path URL `/WebGoat/access-control/user-hash`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%205.JPG)

- Klik kanan request tersebut dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%206.JPG)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%207.JPG)

- Dari task sebelumnya, terdapat 2 endpoint yang tersembunyi yaitu `/users` dan `/config`. Jadi kita bisa mengubah request dari **POST /WebGoat/access-control/user-hash** menjadi **GET /WebGoat/access-control/users**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%208.JPG)

- Kemudian ubah Content-Type dari **application/x-www-form-urlencoded** menjadi **application/json**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%209.JPG)

- Jika sudah tekan tombol **Send** maka akan tampil userHash dari user **Jerry**

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2010.JPG)

- **Pertanyaan:** Start with the information you already gathered (hidden menu items) to see if you can pull the list of users and then provide the 'hash' for Jerry’s account.

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2011.JPG)

- **Jawaban**
```sh
SVtOlaa+ER+w2eoIIVE5/77umvhcsh5V8UyDLUa1Itg=
```

## The company fixed the problem, right?
- Endpoint `/users-admin-fix` hanya bisa diakses oleh user admin

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2012.JPG)

- Kita bisa mengecek source code aplikasi untuk membantu menyelesaikan task ini. Di file `MissingFunctionACYourHashAdmin.java` (link: https://github.com/WebGoat/WebGoat/blob/main/src/main/java/org/owasp/webgoat/lessons/missingac/MissingFunctionACYourHashAdmin.java ) terdapat syntak untuk mengecek kesamaan hash yang kita input dengan hash user jerry yang tersimpan di system

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2013.JPG)

- Pada file `MissingFunctionAC.java` (link: https://github.com/WebGoat/WebGoat/blob/main/src/main/java/org/owasp/webgoat/lessons/missingac/MissingFunctionAC.java ) terdapat password salt untuk mengenkrip hash

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2014.JPG)

- Pada file `DisplayUser.java` (link: https://github.com/WebGoat/WebGoat/blob/main/src/main/java/org/owasp/webgoat/lessons/missingac/DisplayUser.java ) terdapat function untuk mengenerate hash pada setiap user

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2015.JPG)

- Pada file `V2021_11_03_1__ac.sql` (link: https://github.com/WebGoat/WebGoat/blob/main/src/main/resources/lessons/missingac/db/migration/V2021_11_03_1__ac.sql ) terdapat query untuk membuat tabel `access_control_users` dan mengisi tabel tersebut. Dari file ini terlihat bahwa plaintext dari password user Jerry adalah `doesnotreallymatter`

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2016.JPG)

- Dari informasi diatas, kita akan mengetahui hash user Jerry dengan menerapkan alur serupa. Kita akan menulis program menggunakan bahasa pemrograman java di Kali Linux, untuk itu kita perlu terlebih dahalu meng install jdk dengan perintah dibawah ini
```sh
sudo apt-get install default-jdk
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2017.JPG)

- Jika jdk sudah terinstall, sekarang kita menuliskan script untuk mengetahui hash dari user Jerry. Script yang berhasil kita buat adalah sebagai berikut, simpan dengan nama file `Main.java`
```sh
import java.nio.charset.StandardCharsets;
import java.security.MessageDigest;
import java.util.Base64;

public class Main{
	public static void main(String[] args){
		
		String username = "Jerry";
		String password = "doesnotreallymatter";
		String PASSWORD_SALT_SIMPLE = "DeliberatelyInsecure1234";
  		String PASSWORD_SALT_ADMIN = "DeliberatelyInsecure1235";
		
		try{
			MessageDigest md = MessageDigest.getInstance("SHA-256");
			
			String salted = password + PASSWORD_SALT_SIMPLE + username;
			byte[] hash = md.digest(salted.getBytes(StandardCharsets.UTF_8));
			String result = Base64.getEncoder().encodeToString(hash);
			System.out.println("Hash Jerry (simple salt) : "+result);
			
			salted = password + PASSWORD_SALT_ADMIN + username;
			hash = md.digest(salted.getBytes(StandardCharsets.UTF_8));
			result = Base64.getEncoder().encodeToString(hash);
			System.out.println("Hash Jerry (salt admin) : "+result);
			
		}catch(Exception e){
			System.out.println("Terjadi kesalahan : "+e.getMessage());
		}
		
	}
}
```
- Jika sudah compile program diatas
```sh
javac Main.java
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2018.JPG)

- Setelah proses compile berhasil, kita jalankan program diatas
```sh
java Main
```

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2019.JPG)

- Dari output program diatas, terlihat bahwa hash user Jerry yang menggunakan simple salt adalah hash user Jerry yang kita temukan di task sebelumnya. Sedangkan hash user Jerry yang menggunakan salt admin adalah hash yang digunakan untuk menjawab pertanyaan di task ini
- **Pertanyaan:** Start with the information you already gathered (hidden menu items) to see if you can pull the list of users and then provide the 'hash' for Jerry’s account.

![alt text](https://github.com/rahardian-dwi-saputra/webgoat/blob/main/assets/missing%20function%20level%20access%20control/missing%20function%2020.JPG)

- **Jawaban**
```sh
d4T2ahJN4fWP83s9JdLISio7Auh4mWhFT1Q38S6OewM=
```