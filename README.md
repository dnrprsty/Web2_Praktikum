# Praktikum Web 2 - CodeIgniter 4 dengan Docker Compose

```mermaid
mindmap
  root((Praktikum Web 2))
    Modul 1
      Setup CodeIgniter 4
      Konfigurasi Environment
      Routing
      Controller
      View
      Layout Dasar

    Modul 2
      CRUD Artikel
      Database Connection
      Model Artikel
      Tambah Artikel
      Edit Artikel
      Delete Artikel

    Modul 3
      View Layout
      Template Header Footer
      Sidebar
      View Cell
      Artikel Terkini

    Modul 4
      Authentication
      Login Admin
      Session
      Auth Filter
      Logout

    Modul 5
      Pagination
      Search Artikel
      Filter Data

    Modul 6
      Relasi Tabel
      Query Builder
      Join Artikel dan Kategori
      CRUD Kategori
```

---

## Modul 1 — PHP Framework (CodeIgniter 4)

```mermaid
flowchart TD
    A[Install CodeIgniter 4] --> B[Konfigurasi .env]
    B --> C[Setup Debug Mode]
    C --> D[Routing]
    D --> E[Controller]
    E --> F[View]
    F --> G[Halaman About & Contact]
```

### Implementasi:
- Instalasi CodeIgniter 4
- Konfigurasi `.env`
- Routing dasar
- Pembuatan controller
- Pembuatan halaman statis

### Screenshot:
![Halaman Beranda](ss/home.png)

![Halaman About](ss/about.png)

![Halaman Contact](ss/kontak.png)

---

## Modul 2 — Framework Lanjutan (CRUD)

```mermaid
flowchart TD
    A[Database Artikel] --> B[Model Artikel]
    B --> C[Create]
    C --> D[Read]
    D --> E[Update]
    E --> F[Delete]
```

### Implementasi:
- CRUD Artikel
- Validasi input
- Auto generate slug
- Upload gambar artikel

### Screenshot:
![Daftar Artikel](ss/artikel.png)

![Detail Artikel](ss/detail.png)

![Tambah Artikel](ss/tambah.png)

![Edit Artikel](ss/edit.png)

---

## Modul 3 — View Layout dan View Cell

```mermaid
flowchart LR
    A[Header] --> B[Navigation]
    B --> C[Content]
    C --> D[Sidebar]
    D --> E[Footer]
```

### Implementasi:
- Template layout reusable
- Header & Footer terpisah
- Sidebar dinamis
- View Cell artikel terbaru

### Screenshot:
![Halaman Beranda](ss/home.png)

---

## Modul 4 — Framework Lanjutan (Login)

```mermaid
flowchart TD
    A[Login Form] --> B[Validasi User]
    B --> C[Session]
    C --> D[Dashboard Admin]
    D --> E[Logout]
```

### Implementasi:
- Login admin
- Session authentication
- Middleware Auth Filter
- Logout system

### Screenshot:
![Login Admin](ss/login.png)

![Dashboard Artikel](ss/admin.png)

---

## Modul 5 — Pagination dan Pencarian

```mermaid
flowchart TD
    A[Data Artikel] --> B[Pagination]
    A --> C[Search]
    A --> D[Filter]
```

### Implementasi:
- Pagination artikel publik
- Pagination admin
- Search berdasarkan judul
- Search isi artikel
- Filter kategori

### Screenshot:
![Dashboard Artikel](ss/admin.png)

![Pencarian & Filter](ss/cari.png)

---

## Modul 6 — Relasi Tabel dan Query Builder

```mermaid
erDiagram
    KATEGORI ||--o{ ARTIKEL : memiliki
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
```

### Implementasi:
- Relasi One-to-Many
- Artikel ↔ Kategori
- Query Builder Join
- CRUD kategori
- Validasi delete kategori

### Screenshot:
![Daftar Kategori](ss/daftar.png)

![Tambah Kategori](ss/tambahkat.png)

---

## Workflow Aplikasi

```mermaid
flowchart TD
    A[User Visit Website] --> B[Home Page]
    B --> C[Artikel]
    C --> D[Detail Artikel]

    E[Admin Login] --> F[Dashboard]
    F --> G[Kelola Artikel]
    F --> H[Kelola Kategori]

    G --> I[CRUD Artikel]
    H --> J[CRUD Kategori]
```

---

## Struktur Database

```mermaid
erDiagram
    USERS ||--o{ ARTIKEL : author
    KATEGORI ||--o{ ARTIKEL : kategori
```

---

## Teknologi

```mermaid
flowchart LR
    A[CodeIgniter 4] --> B[PHP 8]
    B --> C[MySQL 8]
    C --> D[Docker Compose]
    D --> E[Apache]
```
