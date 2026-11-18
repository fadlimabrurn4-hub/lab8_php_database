# Praktikum 8: PHP dan Database MySQL - Lab8Web   

Nama : Fadli Mabrur Nahari  
NIM : 312510294  
Kelas : I251A  
Mata Kuliah : Pemrograman Web

## Persiapan

### 1. Menjalankan MySQL Server
Layanan **Apache** dan **MySQL** dinyalakan lewat XAMPP Control Panel. Keduanya harus berstatus *running* agar PHP dan database dapat digunakan.

<img src="foto/ss1.png">  

### 2. Mengakses phpMyAdmin
phpMyAdmin dibuka di `http://localhost/phpmyadmin/` sebagai antarmuka untuk mengelola database MySQL (MariaDB).

<img src="foto/ss2.png">  

## Membuat Database: Studi Kasus Data Barang

### 3. Membuat Database
Database dibuat dengan perintah `CREATE DATABASE latihan1;` lewat MySQL client di terminal.

<img src="foto/ss3.png">  

### 4. Membuat Tabel
Tabel `data_barang` dibuat dengan kolom `id_barang` (primary key, auto increment), `nama`, `kategori`, `gambar`, `harga_beli`, `harga_jual`, dan `stok`.

<img src="foto/ss4.png">  

### 5. Menambahkan Data
Tiga data awal dimasukkan dengan `INSERT INTO` (HP Samsung, HP Xiaomi, dan HP Oppo), lalu diperiksa dengan `SELECT * FROM data_barang;`.

<img src="foto/ss5.png">  
<img src="foto/ss5L.png">  

## Membuat Program CRUD

### 6. Membuat Folder Proyek
Folder `lab8_php_database` dibuat di direktori `htdocs` dan diakses lewat `http://localhost/lab8_php_database/`. Karena belum ada file, Apache menampilkan daftar isi folder (*Index of*).

<img src="foto/ss6.png">  

### 7. Koneksi Database (`koneksi.php`)
File ini menghubungkan PHP ke MySQL dengan `mysqli_connect()` (host `localhost`, user `root`, database `latihan1`). Jika koneksi gagal tampil pesan error dan program dihentikan, jika berhasil tampil "Koneksi berhasil". File ini di-*include* oleh semua halaman lainnya.

<img src="foto/kode1.png">  
<img src="foto/hasil1.png">  

### 8. Menampilkan Data / Read (`index.php`)
Halaman utama menjalankan `SELECT * FROM data_barang`, lalu menampilkan hasilnya dalam tabel dengan perulangan `while` dan `mysqli_fetch_array()`. Jika tabel kosong, muncul tulisan "Belum ada data". Pada versi akhir, kolom Aksi berisi tautan **Ubah** dan **Hapus**, serta ada tautan **Tambah Barang**.

<img src="foto/kode2.png">  
<img src="foto/kode2L.png">  
<img src="foto/hasil2.png">  

### 9. Menambah Data / Create (`tambah.php`)
Halaman berisi form (nama, kategori, harga jual, harga beli, stok, dan file gambar) dengan `method="post"` dan `enctype="multipart/form-data"` agar bisa mengunggah file. Saat tombol **Simpan** ditekan, PHP menyimpan gambar ke folder `gambar/`, menjalankan `INSERT INTO`, lalu mengarahkan kembali ke `index.php`. Pada pengujian ditambahkan barang **Laptop Gaming** (kategori Komputer, stok 21), dan barang tersebut muncul sebagai baris keempat di tabel.

<img src="foto/kode3.png">  
<img src="foto/kode3L.png">  
<img src="foto/kode3L1.png">  
<img src="foto/hasil3.png">  
<img src="foto/hasil3L.png">  
<img src="foto/Hasil3L1.png">  

### 10. Mengubah Data / Update (`ubah.php`)
Halaman ini mengambil `id` dari URL (`ubah.php?id=...`), mengambil datanya dengan `SELECT`, lalu mengisi form dengan nilai lama. Setelah disimpan, `UPDATE ... WHERE id_barang` dijalankan. Gambar hanya diganti bila pengguna memilih file baru. Pada pengujian, data **HP Samsung Android** diubah menjadi **HP Samsung G25 Android** dengan kategori Hand Phone.

<img src="foto/kode4.png">  
<img src="foto/kode4L.png">  
<img src="foto/kode4L1.png">  
<img src="foto/hasil4.png">  
<img src="foto/Hasil3L1.png">  
<img src="foto/hasil4L1.png">  

### 11. Menghapus Data / Delete (`hapus.php`)
Halaman ini mengambil `id` dari URL lalu menjalankan `DELETE FROM data_barang WHERE id_barang`, kemudian kembali ke `index.php`. Pada pengujian, barang **Laptop Gaming** dihapus lewat tautan **Hapus** dan tidak lagi muncul di tabel.

<img src="foto/kode5.png">  
<img src="foto/hasil5.png">  
