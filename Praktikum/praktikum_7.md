# :ledger: Relasi One-to-Many dan Many-to-Many

Disini kumpulan code dan foto hasil Screenshot penerapan praktikum saya di modul 7 Relasi One-to-Many dan Many-to-Many.

## :memo: Dasar Teori

### Relasi

Hubungan antar tabel yang dilakukan dengan pencocokan primary key dengan foreign key untuk mengombinasikan data dari satu tabel dengan tabel lainnya.

### Foreign Key

Properti yang digunakan untuk menandai hubungan dua tabel atau lebih. Foreign key pada tabel anak (child) akan menunjuk tabel induk (parent) yang menjadi referensinya (reference).

### One-to-Many

Relasi yang menunjukkan hubungan antar tabel dimana baris pada tabel induk dapat terhubung dengan satu atau lebih baris di tabel anak. Sementara baris pada tabel anak hanya dapat terhubung dengan satu baris di tabel induk.

Contoh penerapan one-to-many

- Satu tutorial dapat memiliki banyak komentar, namun satu komentar hanya dapat berada di satu tutorial
- Satu dosbing dapat memiliki banyak mahasiswa, namun mahasiswa hanya dapat dibimbing satu dosen

### Many-to-Many

Relasi yang menunjukkan hubungan antar tabel dimana baris pada tabel induk dapat terhubung dengan satu atau lebih baris di tabel anak. Berlaku sebaliknya pada tabel anak yang dapat terhubung dengan satu atau lebih baris di tabel induk.

Contoh penerapan many-to-many

- Satu mahasiswa dapat mengambil banyak mata kuliah, namun satu mata kuliah dapat diambil banyak mahasiswa
- Postingan dapat memiliki banyak tag, namun satu tag dapat dimiliki banyak postingan.

Kombinasi baris pada relasi many-to-many diatur dengan junction table.

### Junction Table

Tabel yang digunakan untuk mengatur kombinasi baris pada relasi many-to-many. Junction table berisi foreign key dari kedua tabel yang memiliki relasi many-to-many.

## :scroll: Langkah Percobaan

### Pembuatan Tabel

Berikut adalah tabel yang akan digunakan pada percobaan ini
posts | comments | tags | post_tag |
--- | --- | --- | --- |
id | id | id | postId |
content (STRING) | review (STRING) | name | tagId |

1. Sebelum membuat migrasi database untuk membuat tabel, pastikan server database sudah aktif dan sudah membuat database dengan nama `lumenpost`.

   <img src="../Screenshot/praktikum_7/1.png" alt="create database" width="800"/>

2. Mengubah konfigurasi database pada file `.env` menjadi seperti gambar dibawah

   <img src="../Screenshot/praktikum_7/2.png" alt="configuration env" width="800"/>

   > [!NOTE]
   > isi nilai dari `DB_PASSWORD` sesuai dengan password database masing-masing.

3. Setelah mengubah konfigurasi pada file `.env`, perlu juga menghidupkan beberapa library bawaan dari lumen dengan membuka file `app.php` pada folder `bootstrap/app.php`, lalu uncomment baris 26 dan 28 seperti pada gambar dibawah.

   <img src="../Screenshot/praktikum_7/3.png" alt="uncommend library" width="800"/>

4. Jalankan command berikut untuk membuat file migration.

   ```
   php artisan make:migration create_posts_table
   php artisan make:migration create_comments_table
   php artisan make:migration create_tags_table
   php artisan make:migration create_post_tag_table
   ```

   <img src="../Screenshot/praktikum_7/4.png" alt="create file migration" width="800"/>

5. Mengubah fungsi `up()` pada beberapa file migrasi yang sudah dibuat sebelumnya, yaitu `create_posts_table`, `create_comments_table`, `create_tags_table`, `create_post_tag_table`. untuk perubahannya bisa dilihat pada gambar dibawah.

   <img src="../Screenshot/praktikum_7/5.png" alt="update func up" width="800"/>

6. Jalankan command `php artisan migrate` untuk eksekusi semua file migration yang sudah dibuat. Hasil eksekusi tersebut adalah pembuatan tabel di database.

   <img src="../Screenshot/praktikum_7/6.1.png" alt="execute migration file" width="800"/>

   <img src="../Screenshot/praktikum_7/6.2.png" alt="table database" width="800"/>

### Pembuatan Model

1. Membuat file dengan nama `Post.php` dalam folder `app/Models/`, lalu isi baris kode seperti pada gambar dibawah.

   <img src="../Screenshot/praktikum_7/7.png" alt="model post" width="800"/>

2. Membuat file dengan nama `Comment.php` dalam folder `app/Models/`, lalu isi baris kode seperti pada gambar dibawah.

   <img src="../Screenshot/praktikum_7/8.png" alt="model comment" width="800"/>

3. Membuat file dengan nama `Tag.php` dalam folder `app/Models/`, lalu isi baris kode seperti pada gambar dibawah.

   <img src="../Screenshot/praktikum_7/9.png" alt="model tag" width="800"/>

### Relasi One-to-Many

1. Menambahkan fungsi `comments()` pada file model `Post.php` yang dibuat pada langkah sebelumnya.

   <img src="../Screenshot/praktikum_7/10.png" alt="add func comment()" width="800"/>

2. Menambahkan fungsi `post()` dan atribut postId pada `$fillable` pada file model `Comment.php` yang dibuat pada langkah sebelumnya.

   <img src="../Screenshot/praktikum_7/11.png" alt="add func post()" width="800"/>

3. Membuat file `PostController.php`, lalu mengisi baris kode sesuai dengan gambar dibawah.

   <img src="../Screenshot/praktikum_7/12.png" alt="create file PostController" width="800"/>

4. Membuat file `CommentController.php`, lalu mengisi baris kode sesuai dengan gambar dibawah.

   <img src="../Screenshot/praktikum_7/13.png" alt="create file CommentController" width="800"/>

5. Menambahkan routes untuk post dan comment dalam path `routes/web.php`. Lalu jalankan aplikasi dengan command `php -S localhost:5000 -t public`

   <img src="../Screenshot/praktikum_7/14.png" alt="add routes" width="800"/>

6. Membuat satu data postingan menggunakan Postman

   <img src="../Screenshot/praktikum_7/15.png" alt="create post" width="800"/>

7. Membuat satu data comment menggunakan Postman

   <img src="../Screenshot/praktikum_7/16.png" alt="create comment" width="800"/>

8. Menampilkan satu data postingan menggunakan Postman

   <img src="../Screenshot/praktikum_7/17.png" alt="get post data" width="800"/>

### Relasi Many-to-Many

1. Menambahkan fungsi `tags()` pada file model `Post.php`

   <img src="../Screenshot/praktikum_7/18.png" alt="add func tags()" width="800"/>

2. Menambahkan fungsi `posts()` pada file model `Tag.php`

   <img src="../Screenshot/praktikum_7/19.png" alt="add func posts()" width="800"/>

3. Membuat file `TagController.php` dan mengisi baris kode seperti pada gambar dibawah.

   <img src="../Screenshot/praktikum_7/20.png" alt="add TagController" width="800"/>

4. Menambahkan fungsi `addTag` dan menambahkan response `tags` pada fungsi `getPostById()` dalam file `PostController.php`, seperti pada gambar dibawah.

   <img src="../Screenshot/praktikum_7/21.png" alt="add func addTag()" width="800"/>

5. Menambahkan routes untuk tag dalam path `routes/web.php`. Lalu jalankan aplikasi dengan command `php -S localhost:5000 -t public`

   <img src="../Screenshot/praktikum_7/22.png" alt="add routes" width="800"/>

6. Membuat satu data tag menggunakan Postman

   <img src="../Screenshot/praktikum_7/23.png" alt="create tag" width="800"/>

7. Menambahkan tag "jadul" pada postingan "disana engkau berdua"

   <img src="../Screenshot/praktikum_7/24.png" alt="add tag for post" width="800"/>

8. Menampilkan satu data postingan "disana engkau berdua" menggunakan Postman.

   <img src="../Screenshot/praktikum_7/25.png" alt="get data post" width="800"/>

9. Membuat satu postingan "tanpamu apa artinya" menggunakan Postman.

   <img src="../Screenshot/praktikum_7/26.png" alt="create data post" width="800"/>

10. Menambahkan tag "jadul" pada postingan "tanpamu apa artinya".

    <img src="../Screenshot/praktikum_7/27.png" alt="add tag for post" width="800"/>

11. Membuat satu tag "lagu" menggunakan Postman.

    <img src="../Screenshot/praktikum_7/28.png" alt="create tag" width="800"/>

12. Menambahkan tag "lagu" pada postingan "tanpamu apa artinya".

    <img src="../Screenshot/praktikum_7/29.png" alt="add tag for post" width="800"/>

13. Menampilkan postingan "disana engkau berada".

    <img src="../Screenshot/praktikum_7/30.png" alt="get post" width="800"/>

14. Menampilkan postingan "tanpamu apa artinya".

    <img src="../Screenshot/praktikum_7/31.png" alt="get post" width="800"/>
