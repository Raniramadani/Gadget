<h1 align="center">GadgetStore</h1>
<h3 align="center">(Pusat Pembelian HP Terpercaya)</h3><br>

<p align="center">
  <img src="public/images/lgo.jpg" alt="Logo unsulbar" width="150" height="auto"><br><br>
</p>

<p align="center">
  <strong>Nama :</strong> Aulia Ramadani <br>
  <strong>NIM :</strong> D0223033
</p>
<br><br>

<p align="center">
  Framework Web laravel <br>
  2025
</p>
<br>

## Tentang GadgetStore

GadgetStore adalah aplikasi web untuk mengelola transaksi penjualan gadget. Aplikasi ini memungkinkan admin untuk mengatur produk, kasir untuk memproses transaksi, dan pelanggan untuk melihat serta membeli produk.

### Role dan fitur-fiturnya

#### 1. Admin (Pengelola aplikasi)

- Manajemen produk (tambah, ubah, hapus)
- Manajemen pengguna
- Lihat riwayat transaksi

#### 2. kasir

- Proses transaksi pembelian
- Cetak struk
- Lihat daftar produk

#### 3. kostumer

- Registrasi & login
- Melihat daftar produk
- Melakukan pemesanan/pembelian


<br>

### Tabel-tabel database beserta field dan tipe datanya
<br>

#### Tabel 1 (Pengguna)

| Field            | Tipe Data | Keterangan             |
|------------------|-----------|------------------------|
| id               | bigint    | Primary key            |
| name             | string    | Nama pengguna          |
| email            | string    | Email unik             |
| password         | string    | Kata sandi             |
| role_id          | bigint    | Relasi ke tabel roles  |
| email_verified_at| timestamp | Verifikasi email       |
| remember_token   | string    | Token login            |
<br>

#### Tabel 2 (Kategori)

| Field | Tipe Data | Keterangan         |
|-------|-----------|--------------------|
| id    | bigint    | Primary key        |
| name  | string    | admin, kasir, customer |
<br>

#### Tabel 3 (Resep)

| Field       | Tipe Data | Keterangan         |
|-------------|-----------|--------------------|
| id          | bigint    | Primary key        |
| name        | string    | Nama produk        |
| description | text      | Deskripsi produk   |
| price       | decimal   | Harga gadget       |
| stock       | integer   | Jumlah stok tersedia |
<br>

#### Tabel 4 (Bahan-bahan)

| Field       | Tipe Data | Keterangan                     |
|-------------|-----------|--------------------------------|
| id          | bigint    | Primary key                    |
| user_id     | bigint    | Relasi ke customer             |
| total_price | decimal   | Total harga seluruh pembelian |
| order_date  | timestamp | Tanggal pemesanan              |
| status      | enum      | Status pesanan (e.g., paid)    |
<br>

### Jenis-jenis Relasi

- Users → Roles (Many-to-One)
- Users → Orders (One-to-Many)
- Orders → Products (Many-to-Many jika ada tabel `order_details`)