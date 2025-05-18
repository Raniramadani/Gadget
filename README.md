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

- Manajemen data produk (tambah, edit, hapus)
- Manajemen pengguna (kasir & customer)
- Melihat dan memantau riwayat transaksi

#### 2. transaksi

- Melayani transaksi pelanggan
- Cetak struk transaksi
- Melihat stok & informasi produk

#### 3. detail transaksi

- Registrasi dan login
- Melihat daftar produk
- Melakukan pembelian


<br>

### Tabel-tabel database beserta field dan tipe datanya
<br>

#### Tabel 1 (users)

| Field              | Tipe Data     | Keterangan                    |
|-------------------|---------------|--------------------------------|
| id                | bigint        | Primary key                   |
| name              | string        | Nama pengguna                 |
| email             | string        | Unik, untuk login             |
| password          | string        | Kata sandi terenkripsi        |
| role_id           | unsignedBigInt| Mengacu ke tabel roles        |
| email_verified_at | timestamp     | Waktu verifikasi email        |
| remember_token    | string        | Token sesi login              |
| timestamps        | timestamps    | created_at & updated_at       |
<br>

#### Tabel 2 (products)

| Field       | Tipe Data | Keterangan                  |
|-------------|-----------|-----------------------------|
| id          | bigint    | Primary key                 |
| name        | string    | Nama produk gadget          |
| description | text      | Deskripsi produk            |
| price       | decimal   | Harga satuan produk         |
| stock       | integer   | Jumlah stok tersedia        |
| brand       | string    | Merek produk                |
| model       | string    | Model produk                |
| image       | string    | Nama file gambar (nullable) |
| timestamps  | timestamps| created_at & updated_at     |
<br>

#### Tabel 3 (transactions)

| Field           | Tipe Data | Keterangan                         |
|-----------------|-----------|------------------------------------|
| id              | bigint    | Primary key                        |
| user_id         | foreignId | Mengacu ke tabel `users` (kasir)   |
| transaction_date| datetime  | Waktu transaksi                    |
| total_amount    | decimal   | Total pembayaran                   |
| status          | string    | Status transaksi (e.g., pending)   |
| timestamps      | timestamps| created_at & updated_at            |
<br>

#### Tabel 4 (transaction_details)

| Field         | Tipe Data | Keterangan                              |
|---------------|-----------|-----------------------------------------|
| id            | bigint    | Primary key                             |
| transaction_id| foreignId | Relasi ke tabel `transactions`          |
| product_id    | foreignId | Relasi ke tabel `products`              |
| quantity      | integer   | Jumlah produk yang dibeli               |
| price         | decimal   | Harga per item saat transaksi           |
| timestamps    | timestamps| created_at & updated_at                 |
<br>

### Jenis-jenis Relasi

- **Users** → **Transactions**: One-to-Many (kasir bisa punya banyak transaksi)
- **Transactions** → **TransactionDetails**: One-to-Many
- **Products** → **TransactionDetails**: One-to-Many
- **Users** → **Roles** *(jika ditambahkan nanti)*: Many-to-One