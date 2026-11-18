# Lab8Web - Praktikum 8: PHP dan Database MySQL

**Nama**  : (isi nama kamu)
**NIM**   : (isi NIM kamu)
**Kelas** : (isi kelas kamu)
**Mata Kuliah** : Pemrograman Web

## Tujuan Praktikum
1. Mahasiswa mampu memahami konsep dasar Database.
2. Mahasiswa mampu memahami konsep dasar CRUD menggunakan PHP.
3. Mahasiswa mampu membuat program CRUD sederhana menggunakan PHP.

## Instruksi Praktikum
1. Persiapkan text editor misalnya VSCode.
2. Buat folder baru dengan nama `lab8_php_database` pada docroot webserver (`htdocs`).
3. Ikuti langkah-langkah praktikum yang dijelaskan berikutnya.

---

## Soal 1: Menjalankan MySQL Server
**Soal:** Pastikan MySQL Server dapat dijalankan melalui XAMPP Control Panel.

**Pengerjaan:** Membuka XAMPP Control Panel, lalu menekan tombol **Start** pada Apache dan MySQL sampai keduanya berwarna hijau.

**Screenshot:**

![XAMPP Control](screenshots/01_xampp.png)

---

## Soal 2: Mengakses MySQL Client menggunakan phpMyAdmin
**Soal:** Pastikan Apache dan MySQL sudah berjalan, kemudian buka `http://localhost/phpmyadmin/` melalui browser.

**Pengerjaan:** Membuka alamat tersebut di browser sehingga tampil halaman phpMyAdmin.

**Screenshot:**

![phpMyAdmin](screenshots/02_phpmyadmin.png)

---

## Soal 3: Membuat Database dan Tabel (Studi Kasus Data Barang)
**Soal:** Buat database `latihan1` dan tabel `data_barang` dengan struktur berikut.

| Nama Field | Tipe Data | Ukuran | Keterangan |
|---|---|---|---|
| id_barang | INT | 10 | Primary Key, Autoincrement |
| kategori | Varchar | 30 | |
| nama | Varchar | 30 | |
| gambar | Varchar | 100 | |
| harga_beli | INT/Decimal | 10 | |
| harga_jual | INT/Decimal | 10 | |
| stok | INT | 4 | |

**Pengerjaan:** Menjalankan query berikut pada tab SQL di phpMyAdmin.

```sql
CREATE DATABASE latihan1;

CREATE TABLE data_barang (
  id_barang int(10) auto_increment Primary Key,
  kategori varchar(30),
  nama varchar(30),
  gambar varchar(100),
  harga_beli decimal(10,0),
  harga_jual decimal(10,0),
  stok int(4)
);
```

**Screenshot:**

![Membuat database dan tabel](screenshots/03_buat_tabel.png)

---

## Soal 4: Menambahkan Data
**Soal:** Tambahkan 3 data barang ke tabel `data_barang`.

**Pengerjaan:**

```sql
INSERT INTO data_barang (kategori, nama, gambar, harga_beli, harga_jual, stok)
VALUES ('Elektronik', 'HP Samsung Android', 'hp_samsung.jpg', 2000000, 2400000, 5),
('Elektronik', 'HP Xiaomi Android', 'hp_xiaomi.jpg', 1000000, 1400000, 5),
('Elektronik', 'HP OPPO Android', 'hp_oppo.jpg', 1800000, 2300000, 5);
```

**Screenshot:**

![Data barang](screenshots/04_data_barang.png)

---

## Soal 5: Membuat Folder Program CRUD
**Soal:** Buat folder `lab8_php_database` pada root directory web server (`C:\xampp\htdocs`), lalu akses melalui `http://localhost/lab8_php_database/`.

**Pengerjaan:** Membuat folder di `htdocs` dan membukanya di browser.

**Screenshot:**

![Folder lab8](screenshots/05_folder.png)

---

## Soal 6: Membuat File Koneksi Database
**Soal:** Buat file `koneksi.php`, lalu uji koneksi database melalui browser.

**Pengerjaan:** File berisi `mysqli_connect()` dengan host `localhost`, user `root`, password kosong, dan database `latihan1`. Untuk pengujian, perintah `echo "Koneksi berhasil";` di-uncomment sementara.

```php
<?php
$host = "localhost";
$user = "root";
$pass = "";
$db   = "latihan1";

$conn = mysqli_connect($host, $user, $pass, $db);
if ($conn == false)
{
    echo "Koneksi ke server gagal.";
    die();
} #else echo "Koneksi berhasil";
?>
```

**Screenshot:**

![Tes koneksi](screenshots/06_koneksi.png)

---

## Soal 7: Menampilkan Data (Read) - index.php
**Soal:** Buat file `index.php` untuk menampilkan data barang dalam bentuk tabel.

**Pengerjaan:** Menjalankan query `SELECT * FROM data_barang`, lalu menampilkan hasilnya dengan perulangan `while` dan `mysqli_fetch_array()`. Setiap baris memiliki link Ubah dan Hapus, dan di atas tabel ada link Tambah Barang. Kode lengkap ada di file `index.php`.

**Screenshot:**

![Tampilan index](screenshots/07_index.png)

---

## Soal 8: Menambah Data (Create) - tambah.php
**Soal:** Buat file `tambah.php` berisi form untuk menambah data barang, termasuk upload gambar.

**Pengerjaan:** Form mengirim data dengan method POST dan `enctype="multipart/form-data"`. Gambar dipindahkan ke folder `gambar/` dengan `move_uploaded_file()`, lalu data disimpan dengan query `INSERT INTO`. Setelah itu halaman diarahkan ke `index.php`. Kode lengkap ada di file `tambah.php`.

**Screenshot form:**

![Form tambah barang](screenshots/08_tambah.png)

**Screenshot hasil (data baru muncul di index):**

![Hasil tambah](screenshots/08b_hasil_tambah.png)

---

## Soal 9: Mengubah Data (Update) - ubah.php
**Soal:** Buat file `ubah.php` berisi form untuk mengubah data barang.

**Pengerjaan:** Data lama diambil berdasarkan `id` dari URL, ditampilkan di form, lalu disimpan dengan query `UPDATE ... WHERE id_barang = ...`. Kode lengkap ada di file `ubah.php`.

**Screenshot form:**

![Form ubah barang](screenshots/09_ubah.png)

**Screenshot hasil (data berubah di index):**

![Hasil ubah](screenshots/09b_hasil_ubah.png)

---

## Soal 10: Menghapus Data (Delete) - hapus.php
**Soal:** Buat file `hapus.php` untuk menghapus data barang.

**Pengerjaan:**

```php
<?php
include_once 'koneksi.php';
$id = $_GET['id'];
$sql = "DELETE FROM data_barang WHERE id_barang = '{$id}'";
$result = mysqli_query($conn, $sql);
header('location: index.php');
?>
```

**Screenshot sebelum dihapus:**

![Sebelum hapus](screenshots/10_sebelum_hapus.png)

**Screenshot sesudah dihapus:**

![Sesudah hapus](screenshots/10b_sesudah_hapus.png)

---

## Kesimpulan
Dari praktikum ini saya dapat membuat aplikasi CRUD sederhana menggunakan PHP dan MySQL, mulai dari membuat database dan tabel, menghubungkan PHP ke database, sampai menampilkan, menambah, mengubah, dan menghapus data.
