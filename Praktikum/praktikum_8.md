# :ledger: Register, Authentication dan Authorization

Disini kumpulan code dan foto hasil Screenshot penerapan praktikum saya di modul 8 Register, Authentication dan Authorization.

## :memo: Dasar Teori

### Authentication

Otentifikasi adalah proses untuk mengenali identitas dengan mekanisme pengasosiasian permintaan yang masuk dengan satu set kredensial pengidentifikasi. Kredensial yang diberikan akan dibandingkan dengan database informasi pengguna yang berwenang di dalam sistem operasi lokal atau server otentifikasi.

### Token

Token merupakan nilai yang digunakan untuk mendapatkan akses ke sumber daya yang dibatasi secara elektronik. Penggunaan token ditujukan pada web service yang tidak menyimpan state yang berkaitan dengan penggunaan aplikasi (stateless) seperti session.

### Authorization

Authorization merupakan proses pemberian hak istimewa yang dilakukan setelah proses authentication. Setelah pengguna diidentifikasi pada proses authentication, authorization akan memberikan hak istimewa dan tindakan yang diizinkan kepada pengguna yang ditentukan.

## :scroll: Langkah Percobaan

### Register

1. Pastikan terdapat tabel users yang sudah dibuat pada bab 3 **Basic Routing dan Migration**.

   <img src="../Screenshot/praktikum_8/1.png" alt="users table" width="800"/>

2. Pastikan sudah terdapat model **User.php** yang digunakan pada bab 5 **Model, Controller, dan Request-Response Handler**.

   <img src="../Screenshot/praktikum_8/2.png" alt="model user" width="800"/>

3. Membuat file **AuthController.php** dengan isian baris kode seperti dibawah.

   <img src="../Screenshot/praktikum_8/3.png" alt="auth controller" width="800"/>

4. Menambahkan routes baru di `routes/web.php`

   <img src="../Screenshot/praktikum_8/4.png" alt="routes" width="800"/>

5. Menjalankan aplikasi dan mencoba endpoint `/auth/register` dengan request body seperti dibawah.

   <img src="../Screenshot/praktikum_8/5.png" alt="execute endpoint" width="800"/>

### Authentication

1. Membuat fungsi `login(Request $request)` pada file **AuthController.php**

   <img src="../Screenshot/praktikum_8/6.png" alt="func login" width="800"/>

2. Menambahkan routes baru di `routes/web.php`

   <img src="../Screenshot/praktikum_8/7.png" alt="routes" width="800"/>

3. Menjalankan aplikasi dan mencoba endpoint `/auth/login` dengan request body email dan password yang sesuai

   <img src="../Screenshot/praktikum_8/8.png" alt="execute endpoint" width="800"/>

4. Mengeksekusi endpoint `auth/login` dengan request body email yang salah, tetapi password yang benar

   <img src="../Screenshot/praktikum_8/8.1.png" alt="execute endpoint" width="800"/>

5. Mengeksekusi endpoint `auth/login` dengan request body email yang benar, tetapi password yang salah

   <img src="../Screenshot/praktikum_8/8.2.png" alt="execute endpoint" width="800"/>

### Token

1. Membuat file migrasi baru dengan menjalankan perintah seperti pada gambar dibawah

   <img src="../Screenshot/praktikum_8/9.png" alt="create file migration" width="800"/>

2. Menambahkan baris kode pada file migration yang baru terbuat

   <img src="../Screenshot/praktikum_8/10.png" alt="edit file migration" width="800"/>

3. Menambahkan atribut token pada `$fillable` di file **User.php**

   <img src="../Screenshot/praktikum_8/11.png" alt="add token variable" width="800"/>

4. Menambahkan baris kode pada file **AuthController.php**

   <img src="../Screenshot/praktikum_8/12.png" alt="edit auth controller" width="800"/>

5. Mengeksekusi file migrasi yang sudah dibuat dengan command `php artisan migrate`

   <img src="../Screenshot/praktikum_8/13.png" alt="execute file migration" width="800"/>

6. Menjalankan aplikasi dan mencoba endpoint `/auth/login` dengan request body seperti dibawah, serta menyalin token dari response jika sukses login.

   <img src="../Screenshot/praktikum_8/14.png" alt="execute endpoint" width="800"/>

### Authorization

1. Membuat file **Authorization.php** pada folder di path `App/Http/Middleware` dan mengisi baris kode seperti pada gambar dibawah.

   <img src="../Screenshot/praktikum_8/15.png" alt="create authorization" width="800"/>

2. Menambahkan middleware sudah dibuat pada `bootstrap/app.php`

   <img src="../Screenshot/praktikum_8/16.png" alt="add middleware" width="800"/>

3. Membuat fungsi `home()` pada **HomeController.php**

   <img src="../Screenshot/praktikum_8/17.png" alt="create func home" width="800"/>

4. Memambahkan routes baru pada `routes/web.php`

   <img src="../Screenshot/praktikum_8/18.png" alt="create routes" width="800"/>

5. Menjalankan aplikasi dan mencoba endpoint `/home` dengan melampirkan nilai token yang didapatkan dari login user pada **headers**

   <img src="../Screenshot/praktikum_8/19.png" alt="execute endpoint" width="800"/>
