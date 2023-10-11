# :ledger: Model, Controller, dan Request-Response Handler

Disini kumpulan code dan foto hasil Screenshot penerapan praktikum saya di modul 3 MongoDB dan Express.

## :memo: Dasar Teori

### Model

Model merupakan bagian yang bertugas untuk menyiapkan, mengatur, memanipulasi, dan mengorganisasikan data yang ada di database. Model merepresentasikan kolom apa saja yang ada pada databas, termasuk relasi dan primary key dapat didefinisikan di dalam model. Dengan menggunakan perintah Artisan, pembuatan model pada Laravel dapat dilakukan dengan satu perintah menggunakan

```
php artisan make:model nama_model
```

Namun karena perintah Artisan yang terbatas pada Lumen, pembuatan model harus dilakukan secara manual.

### Controller

Controller merupakan bagian yang menjadi tempat berkumpulnya logika pemrograman yang digunakan untuk memisahkan organisasi data pada database. Dalam beberapa kasus, controller menjadi penghubung antara model dan view pada arsitektur MVC

### Request Handler

Request handler adalah fungsi yang digunakan untuk berinteraksi dengan request yang datang. Request handler dapat digunakan untuk melihat apa saja yang dikirimkan oleh user seperti parameter, query, dan body.

### Response Handler

Response handler adalah fungsi yang digunakan untuk membentuk output yang diharapkan kepada user dan beberapa properti selain data seperti status code dan header.

## :scroll: Langkah Percobaan

### Model

1. Pastikan terdapat tabel users yang dibuat menggunakan migration pada bab sebelumnya.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="../Screenshot/praktikum_6/1.png" alt="table user" width="600"/>

2. Melakukan edit model `User.php` yang ada di dalam path `app/Models/`

   <img src="../Screenshot/praktikum_6/2.png" alt="model user" width="600"/>

### Controller

1. Salin **ExampleController.php** pada folder `app/Http/Controllers`, ganti namanya menjadi **HomeController.php** dan membuat fungsi `index()`.

   <img src="../Screenshot/praktikum_6/3.png" alt="home controller" width="600"/>

2. Mengubah route `/` pada file `routes/web.php` menjadi seperti gambar dibawah

   <img src="../Screenshot/praktikum_6/4.png" alt="edit routes /" width="600"/>

3. Menjalankan aplikasi untuk melihat hasilnya.

   <img src="../Screenshot/praktikum_6/5.png" alt="run" width="600"/>

### Request Handler

1. Melakukan import library Request, setelah itu merubah fungsi index dalam file `HomeController.php` menjadi seperti pada gambar dibawah dan mencoba menjalankan aplikasi untuk melihat hasilnya.

   <img src="../Screenshot/praktikum_6/6.png" alt="request execution" width="600"/>

### Response Handler

1. Melakukan import library Response dan membuat fungsi `hello()` dalam file `HomeController.php`seperti pada gambar dibawah.

   <img src="../Screenshot/praktikum_6/7.png" alt="response handler" width="600"/>

2. Menambahkan route `/hello` pada file `routes/web.php`

   <img src="../Screenshot/praktikum_6/8.png" alt="add route hello" width="600"/>

3. Menjalankan aplikasi untuk melihat hasilnya.

   <img src="../Screenshot/praktikum_6/9.png" alt="run app" width="600"/>

## :open_book: Penerapan

1. Melakukan import model User ke dalam file `HomeController.php`.

   <img src="../Screenshot/praktikum_6/10.png" alt="import library" width="600"/>

2. Menambahkan ketiga fungsi seperti pada gambar dibawah di dalam `HomeController.php`.

   <img src="../Screenshot/praktikum_6/11.png" alt="add function" width="600"/>

3. Menambahkan ketiga route pada file `routes/web.php` dengan menggunakan group route.

   <img src="../Screenshot/praktikum_6/12.png" alt="add routes" width="600"/>

4. Mencoba menjalankan endpoint `users/default` dengan menggunakan Postman untuk melihat hasilnya.

   <img src="../Screenshot/praktikum_6/13.png" alt="eksekusi endpoint users/default" width="600"/>

   <img src="../Screenshot/praktikum_6/13_2.png" alt="hasil eksekusi" width="600"/>

5. Mencoba menjalankan endpoint `users/new` dengan mengisi body seperti pada gambar dibawah menggunakan postman.

   <img src="../Screenshot/praktikum_6/14.png" alt="eksekusi endpoint users/new" width="600"/>

   <img src="../Screenshot/praktikum_6/14_2.png" alt="hasil eksekusi" width="600"/>

6. Mencoba menjalankan endpoint `users/all`.
   
   <img src="../Screenshot/praktikum_6/15.png" alt="eksekusi endpoint users/all" width="600"/>


