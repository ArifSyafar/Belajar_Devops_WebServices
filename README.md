# REST API - Praktikum DevOps & Web Services

Project RESTf API sederhana berbasis PHP Native (MySQLi) dan MySQL menggunakan Laragon untuk memenuhi tugas praktikum DevOps dan Web Services.

## Struktur Project

```text
restapi-NIM/
├── .htaccess          # Pengaturan URL Rewrite
├── connection.php     # Konfigurasi koneksi database MySQLi
└── api-karyawan.php   # Endpoint CRUD Data Karyawan
```

## Cara Menjalankan Project (Laragon)

### 1. Clone atau Download Repository

Clone repository atau ekstrak folder project ke direktori web server Laragon:

```text
C:\laragon\www\restapi-NIM\
```

### 2. Jalankan Laragon

1. Buka aplikasi Laragon.
2. Klik **Start All** untuk menjalankan Apache dan MySQL.

### 3. Konfigurasi Database

1. Buka HeidiSQL atau phpMyAdmin.
2. Buat database baru dengan nama `db_cloudpnm`.
3. Jalankan query SQL berikut untuk membuat tabel `tbl_karyawan`.

```sql
CREATE TABLE tbl_karyawan (
    id INT(11) NOT NULL AUTO_INCREMENT,
    nama VARCHAR(50) DEFAULT NULL,
    jenis_kelamin ENUM('Laki-laki', 'Perempuan') DEFAULT NULL,
    handphone VARCHAR(15) DEFAULT NULL,
    alamat VARCHAR(100) DEFAULT NULL,
    PRIMARY KEY ('id')
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;
```

**Catatan:** Pastikan konfigurasi database pada `connection.php` sesuai dengan pengaturan MySQL di Laragon.

### 4. Uji Coba API

Gunakan Postman untuk menguji endpoint berikut:

**Base URL:**

```text
http://localhost/restapi-NIM/api-karyawan
```

Pastikan Apache, MySQL, dan konfigurasi URL Rewrite sudah berjalan dengan benar.

## Daftar Endpoint API

API menggunakan parameter `function` pada query string untuk menentukan operasi CRUD.

| Aksi | Method | Endpoint | Deskripsi |
|---|---|---|---|
| Get All | `GET` | `?function=getKaryawan` | Menampilkan seluruh data karyawan |
| Get By ID | `GET` | `?function=getKaryawanById&id=1` | Menampilkan data karyawan berdasarkan ID |
| Insert | `POST` | `?function=insertKaryawan` | Menambahkan data karyawan baru |
| Update | `POST` | `?function=updateKaryawan&id=1` | Memperbarui data karyawan berdasarkan ID |
| Delete | `DELETE` | `?function=deleteKaryawan&id=1` | Menghapus data karyawan berdasarkan ID |

**Contoh penggunaan endpoint:**

```text
GET    http://localhost/restapi-NIM/api-karyawan?function=getKaryawan

GET    http://localhost/restapi-NIM/api-karyawan?function=getKaryawanById&id=1

POST   http://localhost/restapi-NIM/api-karyawan?function=insertKaryawan

POST   http://localhost/restapi-NIM/api-karyawan?function=updateKaryawan&id=1

DELETE http://localhost/restapi-NIM/api-karyawan?function=deleteKaryawan&id=1
```

## Teknologi yang Digunakan

- **PHP Native** — Bahasa pemrograman backend.
- **MySQL** — Sistem manajemen basis data.
- **MySQLi** — Koneksi dan interaksi PHP dengan database.
- **Apache** — Web server melalui Laragon.
- **Postman** — Pengujian endpoint REST API.
- **Git & GitHub** — Version control dan penyimpanan repository.

## Tujuan Project

Project ini dibuat untuk mempelajari implementasi REST API, operasi CRUD (*Create, Read, Update, Delete*), koneksi database MySQL, serta pengujian web services menggunakan Postman.
