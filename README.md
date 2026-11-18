# Lab8Web - Praktikum 8: PHP dan Database MySQL

Nama  : (isi nama)
NIM   : (isi NIM)
Kelas : (isi kelas)

## 1. Menjalankan Apache dan MySQL
Buka XAMPP Control Panel, klik **Start** pada Apache dan MySQL.

![XAMPP](screenshots/01_xampp.png)

## 2. Membuat Database dan Tabel (phpMyAdmin)
Buka http://localhost/phpmyadmin/, buat database `latihan1`, lalu jalankan query `CREATE TABLE data_barang` pada tab SQL.

![phpMyAdmin](screenshots/02_phpmyadmin.png)

## 3. Menambahkan Data Awal
Jalankan query `INSERT INTO` pada tab SQL. Hasilnya dicek dengan `SELECT * FROM data_barang;`.

![Data Barang](screenshots/03_data_barang.png)

## 4. Membuat Folder Project
Folder `lab8_php_database` dibuat di `C:\xampp\htdocs`, diakses lewat http://localhost/lab8_php_database/

![Folder](screenshots/04_folder.png)

## 5. File koneksi.php
Berisi koneksi ke MySQL memakai `mysqli_connect()`. Diuji lewat http://localhost/lab8_php_database/koneksi.php

![Koneksi](screenshots/05_koneksi.png)

## 6. index.php (Read)
Menampilkan seluruh data dari tabel `data_barang` dalam bentuk tabel HTML, dengan link Tambah, Ubah, dan Hapus.

![Index](screenshots/06_index.png)

## 7. tambah.php (Create)
Form untuk menambah barang baru, termasuk upload gambar ke folder `gambar/`.

![Tambah](screenshots/07_tambah.png)

## 8. ubah.php (Update)
Form untuk mengubah data barang berdasarkan `id_barang`.

![Ubah](screenshots/08_ubah.png)

## 9. hapus.php (Delete)
Menghapus data berdasarkan `id_barang`, lalu kembali ke `index.php`.

![Hapus](screenshots/09_hapus.png)
