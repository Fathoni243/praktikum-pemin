# :ledger: JSON Web Token (JWT)

Disini kumpulan code dan foto hasil Screenshot penerapan praktikum saya di modul 9 JSON Web Token (JWT).

## :memo: Dasar Teori

### JSON Web Token

JSON Web Token (JWT) adalah standar terbuka yang mendefinisikan cara ringkas dan mandiri untuk transmisi informasi antar pihak secara aman dalam bentuk objek JSON. Informasi ini dapat diverifikasi karena ditandatangani secara digital menggunakan secret key (dengan algoritma HMAC) atau pasangan kunci publik/pribadi menggunakan RSA atau ECSDA

#### Penggunaan

- Authorization <br/>
  Setelah user masuk, setiap request perlu menyertakan. Hal ini mengizinkan user untuk mengakses route, service, dan resource yang diizinkan menggunakan token.
- Information Exchange <br/>
  JWT dapat digunakan untuk mengamankan transmisi data antar pihak. Hal ini dimungkinkan karena JWT dapat ditandatangani untuk memastikan data dikirimkan oleh pengirim yang benar. Penggunaan signature yang dihitung dengan header dan payload dapat memverifikasi data yang dikirimkan tidak diubah di tengah jalan.

### Struktur

JSON Web Token menggunakan pola berikut. Header, payload, signature dipisahkan dengan titik.

```
xxxxx.yyyyy.zzzzz
```

- Header <br/>
  Berisi algoritma yang digunakan serta jenis token.

  ```
  {
    "alg": "HS256",
    "typ": "JWT"
  }
  ```

  Data di atas akan di-encode menjadi Base64

  ```
  eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
  ```

- Payload <br/>
  Berisi data yang ditransmisikan. Walaupun JWT memastikan dapat yang dikirim tidak diubah, Base64 yang digunakan dapat di-decode. Hal ini membuat JWT tidak dapat digunakan untuk transmisi data rahasia seperti plain text password.

  Data di atas akan di-encode menjadi Base64

  ```
  eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6Ik5pbG91IiwiaWF0IjoxNTE2MjM5MDIyfQ
  ```

- Signature <br/>
  Hasil penandatanganan yang dilakukan dengan header dan payload yang sudah di-encode diikuti dengan secret key menggunakan algoritma yang didefinisikan di header.

  Proses penandatanganan menggunakan rumus sebagai berikut

  ```
  HMACSHA256(
    base64UrlEncode(header) + "." +
    base64UrlEncode(payload),
    secret)
  ```

  Yang menghasilkan signature sebagai berikut

  ```
  58_9vUl1BQN7Fpqs7u7r4tyJC_wvFJ5n4GibGTVnGpU
  ```

## :scroll: Langkah Percobaan

### Penyesuaian Database

1. Melakukan perubahan pada length kolom token dengan menghapus parameter 72 di belakangnya.

   ```
   // from this
   public function up()
   {
       Schema::table('users', function (Blueprint $table) {
           $table->string('token', 72)->unique()->nullable(); //
       });
   }

   // to this
   public function up()
   {
       Schema::table('users', function (Blueprint $table) {
           $table->string('token')->unique()->nullable();
       });
   }
   ```

   <img src="../Screenshot/praktikum_9/1.png" alt="delete length" width="800"/>

2. Menjalankan perintah `php artisan migrate:fresh` untuk memperbaharui migrasi dan menghapus data yang lama.

   <img src="../Screenshot/praktikum_9/2.png" alt="migrate:fresh" width="800"/>

3. Menjalankan aplikasi pada endpoint /auth/register dengan body request seperti pada gambar dibawah.

   <img src="../Screenshot/praktikum_9/3.png" alt="execute endpoint" width="800"/>

### JWT Manual

1. Menambahkan ketiga fungsi seperti pada gambar pada `AuthController.php`.

   <img src="../Screenshot/praktikum_9/4.png" alt="add 3 function controller" width="800"/>

2. Melakukan perubahan dengan menambahkan beberapa kode pada fungsi login.

   <img src="../Screenshot/praktikum_9/5.png" alt="update login function" width="800"/>

3. Tambahkan keempat fungsi seperti pada gambar pada `Middleware/Authorization.php`

   <img src="../Screenshot/praktikum_9/6.png" alt="add 4 function" width="800"/>

4. Melakukan perubahan pada fungsi handle pada `Middleware/Authorization.php`

   <img src="../Screenshot/praktikum_9/7.png" alt="update handle function" width="800"/>

5. Menjalankan aplikasi pada endpoint `/auth/login` dengan body seperti pada gambar. Serta menyalin token yang didapat ke notepad.

   <img src="../Screenshot/praktikum_9/8.png" alt="execute endpoint" width="800"/>

6. Menjalankan aplikasi pada endpoint `/home` dengan melampirkan nilai token yang sudah di salin ke notepad sebelumnya, dari yang didapat setelah login pada header.

   <img src="../Screenshot/praktikum_9/9.png" alt="execute endpoint home" width="800"/>

### JWT Library

1. Melakukan generate jwt key secara online menggunakan website Djecrety ― Django Secret Key Generator dan memasukkan secret key tersebut pada file `.env` dengan membuat variable baru bernama `JWT_SECRET`.

   <img src="../Screenshot/praktikum_9/10.png" alt="generate jwt key" width="800"/>

2. Melakukan instalasi package jwt firebase dengan menggunakan command `composer require firebase/php-jwt`

   <img src="../Screenshot/praktikum_9/11.png" alt="instalation package jwt" width="800"/>

3. Tambahkan fungsi seperti pada gambar di file `AuthController`.

   <img src="../Screenshot/praktikum_9/12.png" alt="add function" width="800"/>

4. Melakukan perubahan pada fungsi login menjadi seperti pada gambar.

   <img src="../Screenshot/praktikum_9/13.png" alt="update function login" width="800"/>

5. Membuat file `JwtMiddleware.php` dan mengisikan baris code seperti pada gambar.

   <img src="../Screenshot/praktikum_9/14.png" alt="create file jwtMiddleware" width="800"/>

6. Daftarkan middleware yang telah dibuat pada `bootstrap/app.php`

   <img src="../Screenshot/praktikum_9/15.png" alt="register middleware" width="800"/>

7. Tambahkan baris code seperti pada gambar di file `routes/web.php`.

   <img src="../Screenshot/praktikum_9/16.png" alt="add routes" width="800"/>

8. Menjalankan aplikasi pada endpoint `/auth/login` dengan request body seperti pada gambar dan menyalin token yang didapat ke notepad.

   <img src="../Screenshot/praktikum_9/17.png" alt="execute endpoint login" width="800"/>

9. Menjalankan aplikasi pada endpoint `/home` dengan melampirkan nilai token yang sudah di salin ke notepad sebelumnya, dari yang didapat setelah login pada header.

   <img src="../Screenshot/praktikum_9/18.png" alt="execute endpoint home" width="800"/>