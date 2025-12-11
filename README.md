# Grouping System Web Application

Sebuah full-stack web application berbasis **PHP (OOP)**, **MySQL**, dan **AJAX**, yang digunakan untuk mengelola dosen, mahasiswa, grup, event, dan percakapan berbasis thread.  
Aplikasi ini dirancang untuk kebutuhan internal kampus, dengan fitur berbeda untuk **Admin**, **Dosen**, dan **Mahasiswa**.

---

# Features

## Admin
- CRUD Dosen (foto, identitas, pagination)
- CRUD Mahasiswa (foto, identitas, pagination)
- Reset / ganti password
- Dashboard navigasi sederhana

---

## Dosen
- Melihat grup yang dimiliki
- Membuat grup baru (Publik / Privat)
- Mengedit informasi grup
- Menambah / menghapus member (mahasiswa & dosen)
- Membuat dan mengelola event
- Membuat dan mengelola thread diskusi
- Kode pendaftaran grup otomatis

---

## Mahasiswa
- Join grup menggunakan kode unik
- Lihat daftar grup milik sendiri
- Lihat grup publik lainnya
- Keluar dari grup
- Akses detail grup (event, member)
- Ganti password

---

## AJAX Thread & Chat
- Real-time pull (tanpa refresh halaman)
- Bubbles pesan berbeda untuk pengirim vs penerima
- Auto-scroll
- Timestamp & sender identity
- Thread dapat dibuka/ditutup oleh dosen

---

## Database ERD
![ERD](./database/erd.png)

---

# Tech Stack

| Layer | Teknologi |
|-------|-----------|
| Backend | PHP (OOP), MySQL |
| Frontend | HTML, CSS (native) |
| AJAX | jQuery |
| Database Tool | MySQL Workbench |
| Server | Apache (XAMPP) |

---

## 🧩 OOP Class Architecture

Project ini menggunakan pendekatan **Object-Oriented Programming (OOP)** untuk memisahkan logic aplikasi dari tampilan dan memastikan setiap fitur memiliki struktur yang jelas, reusable, dan mudah di-maintain.

Berikut rangkuman class utama yang digunakan:

| Class | Deskripsi | Tanggung Jawab Utama |
|-------|-----------|----------------------|
| **Database.php** | Wrapper koneksi MySQL | Membuka koneksi, menjalankan query, dan mengelola hasil query. |
| **User.php** | Representasi akun pengguna | Login, verifikasi role (Admin/Dosen/Mahasiswa), update password. |
| **Dosen.php** | Entity dosen | CRUD data dosen, upload foto, validasi input. |
| **Mahasiswa.php** | Entity mahasiswa | CRUD data mahasiswa, upload foto, pagination data. |
| **Group.php** | Entity grup | Membuat grup, edit informasi, generate kode pendaftaran otomatis, mengambil detail grup. |
| **GroupMember.php** | Relasi grup–anggota | Menambah/menghapus anggota (dosen/mahasiswa), mengecek status keanggotaan. |
| **Event.php** | Entity event dalam grup | Membuat, mengedit, menghapus event, serta menampilkan daftar event per grup. |
| **Thread.php** | Diskusi / topik percakapan | Membuat thread baru, membuka/menutup thread, mengambil daftar thread aktif. |
| **Chat.php** | Chat berbasis AJAX | Menyimpan pesan, menarik pesan terbaru (polling), memformat data chat. |

### 🔹 Kenapa Menggunakan OOP?
- **Lebih terstruktur** → setiap fitur punya class mandiri.  
- **Lebih mudah di-maintain** → perubahan logic tidak memengaruhi UI.  
- **Reusable** → fungsi-fungsi dapat dipanggil ulang di banyak halaman PHP.  
- **Memisahkan business logic dari view** → pola yang wajib di backend development profesional.  

Dengan pendekatan OOP ini, aplikasi tidak hanya berjalan, tetapi juga **memiliki fondasi arsitektur yang jelas dan scalable**.

---

## Project Structure

### `/src`
Berisi seluruh kode aplikasi:
- `/ajax` — Handler untuk request AJAX (join group, chat, dll.)
- `/class` — Seluruh class OOP untuk entity (User, Group, Event, Member, dll.)
- `/images` — Foto dosen dan mahasiswa
- `index.php` — Halaman utama berdasarkan role login
- `login.php` — Halaman login
- `*.php` — Semua halaman fitur (CRUD, detail grup, event, thread, dsb.)
- `style.css` — Styling utama aplikasi

---

### `/database`
Semua file yang berkaitan dengan basis data:
- `fullstack.sql` — Struktur database + data awal
- `erd.png` — Diagram ERD relasi tabel

---

### `/docs`
Dokumentasi tambahan:
- `/screenshots` — Semua screenshot tampilan aplikasi (admin, dosen, mahasiswa, grup, dsb.)

---

### Root Folder
- `README.md` — Dokumentasi lengkap proyek

---

# Database Design  
ERD tersedia di:


Relasi utama meliputi:
`dosen`, `mahasiswa`, `grup`, `event`, `grup_member`, `thread`, `chat`, dan `user`.

---

# Screenshots

## User Panels

### 🔹 Panel Admin
![Admin Panel](./docs/screenshots/admin-panel.png)

### 🔹 Panel Dosen
![Lecturer Panel](./docs/screenshots/lecturer-panel.png)

### 🔹 Panel Mahasiswa
![Student Panel](./docs/screenshots/student-panel.png)

---

## Group Management & Details

### 🔹 Detail Grup (Dosen)
![Group Detail - Lecturer](./docs/screenshots/detailgroup-lecturer.png)

### 🔹 Detail Grup (Mahasiswa)
![Group Detail - Student](./docs/screenshots/detailgroup-student.png)

### 🔹 Halaman Grup (Mahasiswa)
![Group Page - Student](./docs/screenshots/displaygroup-student.png)

### 🔹 Halaman Grup (Dosen)
![Group List - Lecturer](./docs/screenshots/displaygroup-lecturer.png)

---

## User Management

### 🔹 Daftar Dosen
![Lecturer List](./docs/screenshots/display-lecturer.png)

### 🔹 Daftar Mahasiswa
![Student List](./docs/screenshots/display-student.png)

---

# Cara Menjalankan Aplikasi

1. Clone repository  
2. Pindahkan folder `src/` ke dalam `htdocs` (Jika memakai XAMPP)  
3. Import file database:
database/fullstack.sql

4. Atur konfigurasi database pada:
5. Jalankan Apache & MySQL  
6. Akses aplikasi:
http://localhost/grouping-system/src/login.php

---

# Default Accounts

**Admin**
- Username: `admin`
- Password: `admin`

**Dosen/Mahasiswa**  
- Dibuat otomatis dari data admin (CRUD)

---

# Author
**Agnesha Riby Tjoanda**  
Informatics Engineering — Universitas Surabaya  

---

# License
Open for learning & educational purposes.



