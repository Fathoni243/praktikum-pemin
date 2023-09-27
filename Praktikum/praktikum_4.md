# :ledger: Basic Routing dan Migration

Disini kumpulan code dan foto hasil Screenshot penerapan praktikum saya di modul 4 Basic Routing dan Migration.
## :bookmark: Tujuan
Setelah mengikuti praktikum ini, diharapkan dapat:
1. Melakukan basic routing
2. Mengakses routing
3. melakukan migration ke database

## :scroll: Langkah Percobaan
### Basic Routing dan Akses Routing
1. Menambahkan endpoint dengan method GET pada file web.php pada folder routes, code bisa dilihat pada gambar. Setelah itu, coba jalankan server dengan command 
```
php -S localhost:8000 -t public
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Setelah server dijalankan, buka browser dengan url ```http://localhost:8000/get```, path yang diakses akan berbentuk ```http://{BASE_URL}{PATH}```, jika BASE_URL adalah ```localhost:8000``` dan PATH nya adalah ```/get```, maka url akan berbentuk seperti gambar dibawah.
![add routes and execute endpoint](../Screenshot/praktikum_4/1_routing.png)

2. Menambahkan method POST, PUT, PATCH, DELETE dan OPTIONS pada file web.php, code sama dengan menambahkan method GET pada langkah pertama.
![add method](../Screenshot/praktikum_4/2_add_endpoint.png)

3. Menginstall ekstensi thunder client pada VSCode
![install thunder client](../Screenshot/praktikum_4/3_install_thunder_client.png)

4. Buat Request dengan menekan "New Request" pada ekstensi thunder client. Setelah itu mencoba endpoint yang sudah ditambahkan pada file web.php
![tes endpoint](../Screenshot/praktikum_4/4_tes_endpoint_tc.png)

> [!IMPORTANT]
> Bisa dilihat dalam log di terminal, saya sudah mencoba semua endpoint yang ditambahkan sebelumnya yaitu POST, PUT, PATCH, DELETE, dan OPTIONS 

### Migrasi Database

1. Menyalakan server database dan membuat database dengan nama ```lumenapi```
![create database](../Screenshot/praktikum_4/5_createDatabase.png)

2. Konfigurasi database pada file ```.env``` dengan mengisikan DB_DATABASE atau nama database, DB_USERNAME atau username database, dan DB_PASSWORD atau password database. Isikan sesuai dengan server database masing-masing. Setelah itu perlu menghidupkan beberapa library bawaan dari lumen dengan membuka file app.php pada folder bootstrap, untuk lebih jelasnya bisa dilihat pada gambar.
![configuration env](../Screenshot/praktikum_4/6_configuration_env_app.png)

3. Menjalankan command dibawah ini untuk membuat file migration.
```
php artisan make:migration create_users_table # membuat migrasi untuk tabel users
php artisan make:migration create_products_table # membuat migrasi untuk tabel products
```
> [!NOTE]
> 2 file akan terbuat pada folder ```database/migrations``` dengan format YYYY_MM_DD_HHmmss_nama_migrasi.  

![add file migration](../Screenshot/praktikum_4/7_migration.png)

4. Mengubah fungsi up pada file migrasi ```create_users_table``` dan ```create_products_table``` seperti pada gambar dibawah. Setelah itu jalankan dengan command 
```
php artisan migrate
```
![edit file migration](../Screenshot/praktikum_4/8_execute_migrate.png)

5. Cek database **lumenapi**, seharusnya terbuat 2 tabel, yaitu tabel users dan tabel products
![edit file migration](../Screenshot/praktikum_4/9_result.png)



