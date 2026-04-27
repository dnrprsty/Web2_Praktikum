# Praktikum Web 2 - CodeIgniter 4 dengan Docker Compose

## Nama  : Danur Wenda Prasetiyo  
## Kelas : I241A  
## NIM   : 312410008  

Website portal artikel sederhana berbasis **CodeIgniter 4** yang dikembangkan secara bertahap berdasarkan Praktikum Pemrograman Web 2 (Modul 1–6).  
Project ini mencakup implementasi **routing**, **CRUD**, **template layout**, **autentikasi**, **pagination**, **pencarian**, **filter**, **relasi database**, dan **containerization menggunakan Docker Compose**.

---

# 📚 Daftar Modul Praktikum

```mermaid
mindmap
  root((Web 2 CI4))
    Modul 1
      Instalasi CI4
      Routing
      Controller
      View

    Modul 2
      CRUD Artikel
      Model
      Database

    Modul 3
      Layout Template
      Sidebar
      View Cell

    Modul 4
      Authentication
      Session
      Filter

    Modul 5
      Pagination
      Search
      Filter

    Modul 6
      Relasi Tabel
      Join Query
      CRUD Kategori
```

---

# 🛠 Teknologi yang Digunakan

| Komponen | Teknologi |
|--|--|
| Framework | CodeIgniter 4 |
| Backend | PHP 8.x |
| Database | MySQL 8 |
| Web Server | Apache |
| Container | Docker |
| Orchestration | Docker Compose |
| Dependency Manager | Composer |

---

# 📦 Instalasi & Setup

## Prasyarat

Pastikan sudah terinstall:

- Docker
- Docker Compose
- Git

Cek versi:

```bash
docker --version
docker compose version
git --version
```

---

## Clone Repository

```bash
git clone https://github.com/dnrprsty/Web2_Praktikum.git
cd Web2_Praktikum
```

---

## Build Container

Build semua container:

```bash
docker compose up --build -d
```

Flow Docker:

```mermaid
flowchart TD
    A[Clone Repository] --> B[Build Docker Image]
    B --> C[Run Container]
    C --> D[MySQL Ready]
    D --> E[Composer Install]
    E --> F[Migrate Database]
    F --> G[Seeder Data]
    G --> H[Application Ready]
```

---

## Cek Container

```bash
docker compose ps
```

---

## Melihat Log

```bash
docker compose logs -f app
```

---

## Akses Aplikasi

Web:

```text
http://localhost:8082
```

Database:

```text
localhost:3307
```

---

## Stop Container

```bash
docker compose down
```

---

## Rebuild Ulang

Jika ada perubahan Dockerfile:

```bash
docker compose up --build -d
```

---

# 👤 Akun Default

Seeder otomatis membuat akun admin:

Email:

```text
admin@email.com
```

Password:

```text
admin123
```

Login:

```text
http://localhost:8082/user/login
```

---

# 📘 Modul 1 — Pengenalan Framework CodeIgniter 4

Modul pertama berfokus pada instalasi framework dan memahami konsep MVC.

## Materi:
- Instalasi CodeIgniter 4
- Konfigurasi `.env`
- Routing
- Controller
- View
- Halaman statis

Flow:

```mermaid
flowchart LR
    A[Install CI4] --> B[Config Env]
    B --> C[Routing]
    C --> D[Controller]
    D --> E[View]
```

Implementasi:
- Home Controller
- Page Controller
- About Page
- Contact Page

Screenshot:

![Halaman Beranda](ss/home.png)

![Halaman About](ss/about.png)

![Halaman Contact](ss/kontak.png)

---

# 📘 Modul 2 — CRUD Artikel

Modul kedua berfokus pada operasi CRUD menggunakan database.

Materi:
- Database connection
- Model Artikel
- Insert data
- Update data
- Delete data

Flow:

```mermaid
flowchart TD
    A[Tambah Artikel] --> B[Simpan Database]
    B --> C[Tampil Artikel]
    C --> D[Edit Artikel]
    D --> E[Delete Artikel]
```

Fitur:
- Tambah artikel
- Edit artikel
- Hapus artikel
- Validasi form
- Slug otomatis

Screenshot:

![Daftar Artikel](ss/artikel.png)

![Detail Artikel](ss/detail.png)

![Tambah Artikel](ss/tambah.png)

![Edit Artikel](ss/edit.png)

---

# 📘 Modul 3 — View Layout dan View Cell

Modul ketiga membahas template reusable.

Materi:
- Layout utama
- Header
- Footer
- Sidebar
- View Cell

Flow:

```mermaid
flowchart LR
    A[Header] --> B[Navbar]
    B --> C[Content]
    C --> D[Sidebar]
    D --> E[Footer]
```

Implementasi:
- Template utama
- Sidebar dinamis
- Artikel terbaru

Screenshot:

![Halaman Beranda](ss/home.png)

---

# 📘 Modul 4 — Authentication dan Session

Modul keempat berfokus pada sistem login admin.

Materi:
- Login
- Session
- Middleware
- Logout

Flow:

```mermaid
flowchart TD
    A[Login Form] --> B[Validasi]
    B --> C[Session Create]
    C --> D[Dashboard]
    D --> E[Logout]
```

Fitur:
- Login admin
- Session management
- Auth filter
- Logout

Screenshot:

![Login Admin](ss/login.png)

![Dashboard Artikel](ss/admin.png)

---

# 📘 Modul 5 — Pagination, Search, Filter

Modul kelima berfokus pada pengolahan data lebih lanjut.

Materi:
- Pagination
- Search
- Filter kategori

Flow:

```mermaid
flowchart TD
    A[Artikel] --> B[Pagination]
    A --> C[Search]
    A --> D[Filter]
```

Implementasi:
- Pagination public
- Pagination admin
- Search judul
- Search isi
- Filter kategori

Screenshot:

![Dashboard Artikel](ss/admin.png)

![Pencarian & Filter](ss/cari.png)

---

# 📘 Modul 6 — Relasi Tabel dan Query Builder

Modul keenam membahas relasi database.

Relasi:

```mermaid
erDiagram
    KATEGORI ||--o{ ARTIKEL : memiliki
```

Materi:
- Foreign key
- Join query
- Query Builder
- CRUD kategori

Implementasi:
- Artikel memiliki kategori
- Kategori memiliki banyak artikel
- Validasi delete kategori

Screenshot:

![Daftar Kategori](ss/daftar.png)

![Tambah Kategori](ss/tambahkat.png)

---

# 🌐 Endpoint Aplikasi

## Public Routes

| Method | Endpoint |
|--|--|
| GET | / |
| GET | /about |
| GET | /contact |
| GET | /artikel |
| GET | /artikel/{slug} |

---

## User Routes

| Method | Endpoint |
|--|--|
| GET/POST | /user/login |
| GET | /user/logout |

---

## Admin Routes

| Method | Endpoint |
|--|--|
| GET | /admin/artikel |
| GET/POST | /admin/artikel/add |
| GET/POST | /admin/artikel/edit/{id} |
| GET | /admin/artikel/delete/{id} |
| GET | /admin/kategori |
| GET/POST | /admin/kategori/add |
| GET/POST | /admin/kategori/edit/{id} |
| GET | /admin/kategori/delete/{id} |

---

# 🗄 Struktur Database

```mermaid
erDiagram
    USERS {
        int id
        varchar username
        varchar useremail
        varchar userpassword
    }

    KATEGORI {
        int id_kategori
        varchar nama_kategori
        varchar slug_kategori
    }

    ARTIKEL {
        int id
        varchar judul
        text isi
        varchar gambar
        tinyint status
        varchar slug
        int id_kategori
    }

    KATEGORI ||--o{ ARTIKEL : memiliki
```

---

# 📁 Struktur Project

```mermaid
flowchart TD
    A[web2] --> B[app]
    A --> C[docker]
    A --> D[Dockerfile]
    A --> E[docker-compose.yml]
    A --> F[README.md]
    A --> G[ss]
```

---

# 🔧 Development Commands

Masuk container:

```bash
docker exec -it web2_ci4_app bash
```

Migration:

```bash
php spark migrate
```

Seeder:

```bash
php spark db:seed
```

Logs:

```bash
docker compose logs app
```

---

# 📝 Catatan

- Password menggunakan hash
- Session tersimpan di writable/session
- Logs tersimpan di writable/logs
- Upload file tersimpan di writable/uploads
- Slug otomatis generate
- Delete kategori divalidasi

---

# 📄 Lisensi

Project ini dibuat untuk kebutuhan praktikum dan pembelajaran.
