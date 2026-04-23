# Praktikum Web 2 - CodeIgniter 4 dengan Docker Compose

Project ini mengerjakan alur praktikum Web 2 berbasis CodeIgniter 4 dengan penyesuaian agar berjalan penuh memakai `docker compose`.

Fitur yang sudah dibuat:

- Layout website sederhana dan rapi seperti gaya modul.
- Halaman publik: `Home`, `Artikel`, `About`, `Contact`.
- Sidebar dinamis dengan `View Cell` untuk artikel terbaru.
- Login admin + auth filter.
- CRUD artikel.
- CRUD kategori.
- Relasi tabel `artikel` dan `kategori`.
- Query Builder untuk join artikel dengan kategori.
- Pencarian artikel.
- Filter artikel berdasarkan kategori.
- Pagination di halaman artikel admin dan halaman artikel publik.
- Seeder awal supaya project langsung ada isi.

## Jalankan Project

Karena di mesin ini port `8080`, `8081`, dan `3306` sudah dipakai project lain, project ini saya set ke port berikut:

- Aplikasi: `http://localhost:8082`
- MySQL: `localhost:3307`

Perintah menjalankan:

```bash
docker compose up --build -d
```

Untuk menghentikan:

```bash
docker compose down
```

Saat container `app` pertama kali jalan, script startup akan otomatis:

1. menunggu database siap,
2. menjalankan `composer install`,
3. menjalankan migration,
4. menjalankan seeder data awal.

## Akun Admin Default

- Email: `admin@email.com`
- Password: `admin123`

Login admin ada di:

```text
http://localhost:8082/user/login
```

## Fitur Sesuai Modul

### 1. Layout dan halaman publik

Halaman publik memakai layout utama dengan:

- header,
- navigasi,
- area konten utama,
- sidebar,
- footer.

Sidebar juga menampilkan `Artikel Terkini` lewat `View Cell`.

### 2. CRUD artikel

Admin bisa:

- menambah artikel,
- mengubah artikel,
- menghapus artikel,
- memilih kategori artikel,
- mengatur status `Published` atau `Draft`,
- mengganti sumber gambar artikel.

### 3. Relasi tabel dan Query Builder

Relasi database:

- satu kategori bisa punya banyak artikel,
- artikel menyimpan `id_kategori`,
- data admin dan data publik mengambil nama kategori lewat `join`.

### 4. Pencarian, filter, dan pagination

Di halaman admin artikel tersedia:

- input pencarian judul/isi,
- dropdown filter kategori,
- pagination.

## Struktur Penting

File yang paling sering dipakai:

- `docker-compose.yml`  
  Konfigurasi container aplikasi dan database.

- `Dockerfile`  
  Image PHP + Apache + ekstensi yang dibutuhkan CodeIgniter.

- [`app/.env`](app/.env)  
  Konfigurasi environment aplikasi.

- [`app/app/Config/SiteContent.php`](app/app/Config/SiteContent.php)  
  Tempat tercepat untuk ganti isi statis website.

- [`app/app/Config/Routes.php`](app/app/Config/Routes.php)  
  Routing halaman publik dan admin.

- [`app/app/Controllers/Artikel.php`](app/app/Controllers/Artikel.php)  
  Logika artikel publik dan admin.

- [`app/app/Controllers/Kategori.php`](app/app/Controllers/Kategori.php)  
  Logika kategori admin.

- [`app/app/Controllers/User.php`](app/app/Controllers/User.php)  
  Login dan logout admin.

- [`app/app/Models/ArtikelModel.php`](app/app/Models/ArtikelModel.php)  
  Model artikel + query relasi kategori.

- [`app/app/Models/KategoriModel.php`](app/app/Models/KategoriModel.php)  
  Model kategori.

- [`app/app/Database/Migrations`](app/app/Database/Migrations)  
  Struktur tabel database.

- [`app/app/Database/Seeds`](app/app/Database/Seeds)  
  Data awal artikel, kategori, dan user admin.

- [`app/public/style.css`](app/public/style.css)  
  Semua styling tampilan.

## Bagian yang Mudah Dikustom

### 1. Judul website, isi home, about, contact, widget

Ubah file:

- [`app/app/Config/SiteContent.php`](app/app/Config/SiteContent.php)

Yang bisa diubah di situ:

- nama website,
- tagline,
- footer,
- isi halaman home,
- isi halaman about,
- isi halaman contact,
- link sidebar,
- teks widget sidebar.

### 2. Artikel dan kategori awal

Ubah file seeder:

- [`app/app/Database/Seeds/KategoriSeeder.php`](app/app/Database/Seeds/KategoriSeeder.php)
- [`app/app/Database/Seeds/ArtikelSeeder.php`](app/app/Database/Seeds/ArtikelSeeder.php)

Kalau mau apply ulang:

```bash
docker compose exec app php spark db:seed InitialSeeder
```

### 3. Akun admin default

Ubah file:

- [`app/app/Database/Seeds/UserSeeder.php`](app/app/Database/Seeds/UserSeeder.php)

Lalu jalankan ulang:

```bash
docker compose exec app php spark db:seed UserSeeder
```

### 4. Tampilan website

Ubah file:

- [`app/public/style.css`](app/public/style.css)

Yang bisa kamu ubah cepat:

- warna,
- ukuran container,
- tombol,
- tabel admin,
- layout sidebar,
- kartu artikel.

### 5. Port Docker

Kalau kamu ingin ganti port:

- buka `docker-compose.yml`,
- ubah mapping port service `app` dan `db`,
- sesuaikan juga `app/.env` pada `app.baseURL`.

## Perintah Berguna

Masuk ke container aplikasi:

```bash
docker compose exec app bash
```

Cek route:

```bash
docker compose exec app php spark routes
```

Jalankan migration manual:

```bash
docker compose exec app php spark migrate
```

## Catatan

- Artikel dengan status `Draft` tidak tampil di halaman publik.
- Gambar artikel bisa diisi:
  - nama file/path dari folder `public`, contoh `placeholder.svg`
  - atau URL gambar eksternal.
- Jika ingin data baru dari nol, jalankan:

```bash
docker compose down -v
docker compose up --build -d
```
