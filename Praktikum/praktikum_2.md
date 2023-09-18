# :ledger: Praktikum CRUD MongoDB

Disini kumpulan code dan foto hasil Screenshot penerapan praktikum saya di modul 2 CRUD MongoDB.
## :memo: Dasar Teori
* ### MongoDB Compass
    MongoDB Compass adalah tool berbasis Graphical User Interface (GUI) yang digunakan untuk berinteraksi dengan MongoDB yang terpasang secara on-premise dan MongoDB Atlas yang berbasis cloud. Tool ini dapat melakukan aktivitas dasar seperti CREATE, READ, UPDATE, dan DELETE (CRUD) tanpa berhadapan dengan baris perintah (command line).

* ### MongoDB Shell
    Walaupun dapat melakukan operasi seperti MongoDB Compass, interaksi yang dilakukan MongoDB Shell berbasis Command Line Interface (CLI) sehingga diperlukan baris perintah untuk melakukan aktivitas dasar. MongoDB Shell dapat diakses langsung dari MongoDB Compass atau menggunakan mongosh pada Command Prompt.

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
        
    - Hasil update buku "No Longer Human"
    ![Update buku](../Screenshot/praktikum_2/7_updated_results.png) 


    g. Menghapus buku "I Am a Cat" dengan klik button "delete"
    ![Delete buku](../Screenshot/praktikum_2/8_delete.png)

    - Hasil delete buku "I Am a Cat"
    ![Update buku](../Screenshot/praktikum_2/9_deleted_results.png) 


* ### MongoDB Shell
    a. Melakukan konfigurasi di environtment variable untuk bisa menjalankan command ```mongosh``` di terminal
    ![Konfigurasi mongosh](../Screenshot/praktikum_2/10_mongosh_configuration.png) 


