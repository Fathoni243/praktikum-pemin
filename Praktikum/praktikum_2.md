# :ledger: Praktikum CRUD MongoDB

Disini kumpulan code dan foto hasil Screenshot penerapan praktikum saya di modul 2 CRUD MongoDB.
## :memo: Dasar Teori
* ### MongoDB Compass
    <p style='text-align: justify;'> MongoDB Compass adalah tool berbasis Graphical User Interface (GUI) yang digunakan untuk berinteraksi dengan MongoDB yang terpasang secara on-premise dan MongoDB Atlas yang berbasis cloud. Tool ini dapat melakukan aktivitas dasar seperti CREATE, READ, UPDATE, dan DELETE (CRUD) tanpa berhadapan dengan baris perintah (command line). </p>

* ### MongoDB Shell
    <p style='text-align: justify;'> Walaupun dapat melakukan operasi seperti MongoDB Compass, interaksi yang dilakukan MongoDB Shell berbasis Command Line Interface (CLI) sehingga diperlukan baris perintah untuk melakukan aktivitas dasar. MongoDB Shell dapat diakses langsung dari MongoDB Compass atau menggunakan mongosh pada Command Prompt. </p>

## :scroll: Langkah Percobaan
* ### MongoDB Compass
    a. Melakukan koneksi ke MongoDB menggunakan connection string ``` mongodb://localhost:27017 ``` secara lokal. <br />
    ![Screenshot connection mongoDB Compass](../Screenshot/praktikum_2/1_connection.png)

    b. Membuat Database bookstore dengan melakukan klik "Create Database" <br />
    ![Create Database bookstore](../Screenshot/praktikum_2/2_create_database.png)

    c. Insert data buku pertama dengan melakukan klik "Add Data", pilih "Insert Document", isi data dengan data yang diinginkan, lalu klik "insert" <br />

    > :warning: **MongoDB akan membuat nilai _id secara otomatis**

    ![Insert data buku pertama](../Screenshot/praktikum_2/3_insert_data.png)

    d. Insert data buku kedua dengan cara yang sama <br />
    ![Insert data buku kedua](../Screenshot/praktikum_2/4_insert_data_2.png)

    e. Melakukan pencarian buku dengan ```author : "Osamu Dazai"``` dengan mengisi filter yang diinginkan dan klik button "Find"
    ![Find buku](../Screenshot/praktikum_2/5_find.png)

    f. Update field ```summary``` pada buku "No Longer Human" menjadi ```Buku yang bagus (<NAMA>, <NIM>)``` dengan klik button Edit
    ![Update buku](../Screenshot/praktikum_2/6_update.png)
        
    - Hasil buku "No Longer Human" sudah terupdate
    ![Update buku](../Screenshot/praktikum_2/7_updated_results.png) 


    g. Menghapus buku "I Am a Cat" dengan klik button "delete"
    ![Delete buku](../Screenshot/praktikum_2/8_delete.png)

    - Hasil buku "I Am a Cat" sudah terhapus
    ![Update buku](../Screenshot/praktikum_2/9_deleted_results.png) 


* ### MongoDB Shell
    a. Melakukan konfigurasi di environtment variable untuk bisa menjalankan command ```mongosh``` di terminal
    ![Konfigurasi mongosh](../Screenshot/praktikum_2/10_mongosh_configuration.png)

    b. Koneksi ke MongoDB Server dengan menjalankan command ```mongosh``` di terminal windows
    ![connection mongosh](../Screenshot/praktikum_2/11_mongosh_connection.png)

    c. Menjalankan beberapa command berikut : 
    ![command to use database](../Screenshot/praktikum_2/12_use_dbs_mongosh.png)
    :information_source: **Penjelasan :** 
    - ```show dbs``` : melihat isi database yang ada di server
    - ```use <database_name>``` : berpindah ke database yang diinginkan
    - ```show collection``` :  melihat collection yang ada pada database yang digunakan

    d. Insert satu data dengan command ```db.books.insertOne(<data yang dimasukkan>)```
    ![insertOne data](../Screenshot/praktikum_2/13_insertOne_mongosh.png)

    e. Insert banyak data dengan command ```db.books.insertMany(<data yang dimasukkan>)```
    ![insertMany data](../Screenshot/praktikum_2/14_insertMany_mongosh.png)

    f. Pencarian semua buku dengan command ```db.books.find()```
    ![find data](../Screenshot/praktikum_2/15_findAll_mongosh.png)

    g. Melakukan pencarian buku dengan ```author : "Osamu Dazai"``` dengan command ```db.books.find({<filter yang ingin diisi>})```
    ![find data with argument](../Screenshot/praktikum_2/16_find_mongosh.png)

    h. Update field ```summary``` pada buku "Hujan" menjadi ```Buku yang bagus (<NAMA>, <NIM>)``` dengan command 
    ```db.books.updateOne({<filter>},{$set: {<data yang akan di update>}})```
    ![updateOne data](../Screenshot/praktikum_2/17_updateOne_mongosh.png)

    i. Update field ```publisher``` menjadi "Yen Press" pada beberapa buku menggunakan filter ```author : "Osamu Dazai"``` dengan 
    command ```db.books.updateMany({<filter>}, {$set: {<data yang akan di update>}})``` 
    ![updateMany data](../Screenshot/praktikum_2/18_updateMany_mongosh.png)

    j. Menghapus buku "Overlord I" dengan command ```db.books.deleteOne({<argument>})```
    ![deleteOne data](../Screenshot/praktikum_2/19_deleteOne_mongosh.png)

    k. Menghapus beberapa buku dengan menggunakan filter ```author : "Osamu Dazai"``` dengan command 
    ```db.books.deleteMany({<argument>})```
    ![deleteOne data](../Screenshot/praktikum_2/20_deleteMany_mongosh.png)
