# Toko Papua Online — Halaman Web Toko (Store)

Halaman web toko responsif untuk **Toko Papua Online**, dibangun sebagai satu berkas
`index.html` mandiri (HTML + CSS + JavaScript inline) tanpa dependensi eksternal.

Tampilan dan struktur mengikuti pola halaman store e-commerce modern: header dengan
logo + navigasi + pencarian, banner promo (carousel), baris kategori, grid kartu produk,
baris keunggulan layanan, blok "Tentang", dan footer.

---

## 1. Isi Paket

| File | Keterangan |
|---|---|
| `index.html` | Halaman toko utama (mobile + desktop, satu berkas) |
| `README.md` | Berkas ini — ringkasan proyek |
| `panduan-upload-github.md` | Panduan lengkap 9 bagian: ekstrak ZIP, buat repo, upload (2 metode), aktifkan Pages, verifikasi, update, troubleshooting, FAQ & checklist |
| `.nojekyll` | Menonaktifkan pemrosesan Jekyll di GitHub Pages |
| `images/logo.webp` | Logo toko (header + footer) |
| `images/banner-1.webp` | Banner promo carousel 1 |
| `images/banner-2.webp` | Banner promo carousel 2 |
| `images/produk-1.webp` | Sampul produk 1 |
| `images/produk-2.webp` | Sampul produk 2 |

### Tautan pembelian tiap produk

| # | Produk | Tautan checkout |
|---|---|---|
| 1 | Belanda di Irian Jaya (Pim Schoorl - KITLV) | `https://tokopapuaonline.orderhero.id/form/checkout-belanda-irian-jaya` |
| 2 | Laporan Tindak Kekerasan di Papua - Gugus Tugas UGM | `https://tokopapuaonline.orderhero.id/form/checkout-belanda-irian-jaya` *(sementara — belum ada tautan checkout khusus)* |

⚠️ **Perlu tautan checkout terpisah:** produk **Laporan Tindak Kekerasan di Papua
- Gugus Tugas UGM** **belum memiliki halaman checkout sendiri**. Sudah diuji pada
2026-09-21: `/form/checkout-laporan-tindak-kekerasan-di-papua` dan beberapa varian
slug lain mengarah ke halaman **Not Found**. Karena itu tombol Beli produk ini
sementara diarahkan ke tautan checkout yang sudah tersedia agar tetap berfungsi.
Kirimkan tautan checkout produk tersebut bila sudah tersedia, agar diarahkan ke
halaman yang tepat.

> Paket ini murni berisi halaman web dan asetnya. Halaman diterbitkan langsung pada
> alamat bawaan layanan hosting statis, sehingga tidak diperlukan berkas konfigurasi
> tambahan maupun pengaturan apa pun di sisi Anda.

---

## 2. Fitur

**Responsif penuh (mobile & desktop)**

| | Mobile (≤ 767 px) | Desktop (≥ 768 px) |
|---|---|---|
| Header | Logo + kolom pencarian, tinggi 56 px | Logo + menu navigasi + pencarian + tombol keranjang, tinggi 68 px |
| Navigasi | Bottom tab bar (Home / Produk / Keranjang / Lainnya) | Navigasi teks di header |
| Banner | Carousel 16:9 sudut 12 px | Carousel tinggi 392 px sudut 16 px |
| Kategori | 4 kotak ikon bulat | Pil horizontal dengan ikon + label |
| Grid produk | 2 kolom | 3 kolom (≥ 1100 px: 4 kolom) |
| Footer | Bertumpuk satu kolom | 3 kolom sejajar, tema gelap |

Diverifikasi pada **390 × 844** (mobile) dan **1280 × 900** (desktop), tanpa
overflow horizontal pada keduanya.

**Komponen & interaksi**

- **Carousel banner** — tombol sebelumnya/berikutnya, dot indikator, rotasi otomatis
  (dinonaktifkan bila pengguna mengaktifkan *prefers-reduced-motion*).
- **Filter kategori** — Semua / Promo / Terlaris / Baru.
- **Pencarian produk** — menyaring kartu secara langsung berdasarkan judul dan kategori.
- **Kartu produk** — sampul, judul (maksimal 3 baris), harga, tombol **Beli**
  yang membuka halaman checkout di tab baru (`target="_blank"`, `rel="noopener noreferrer"`).
- **Modal detail produk** — sampul besar, deskripsi, rincian harga, tombol
  *Tambah ke Keranjang* dan *Beli Sekarang*.
- **Keranjang** — panel samping (drawer) dengan penambahan/pengurangan jumlah,
  hapus item, subtotal, dan tombol lanjut ke pembelian.
- **Notifikasi (toast)** — umpan balik saat produk masuk keranjang.
- **Aksesibilitas** — `aria-label`, `aria-pressed`, `aria-hidden`, `role="status"`,
  navigasi papan tuntas keyboard, dan atribut `lang="id"`.

**Tanpa dependensi eksternal**

Seluruh ikon memakai inline SVG sprite, CSS dan JavaScript ditulis langsung di dalam
berkas. Halaman tidak memanggil CDN, font eksternal, atau pustaka pihak ketiga —
sehingga tetap tampil utuh meski dibuka tanpa koneksi ke layanan luar.

---

## 3. Produk

| # | Produk | Kategori | Harga |
|---|---|---|---|
| 1 | E-Book Belanda di Irian Jaya: Amtenar di Masa Penuh Gejolak 1945-1962 (Pim Schoorl - KITLV) | Sejarah Kolonial | Rp 50.000 |
| 2 | E-Book Laporan Tindak Kekerasan di Papua (Januari 2010 - Maret 2022) - Gugus Tugas UGM | Laporan Riset | Rp 50.000 |

Harga di atas adalah **harga produk**. Biaya transaksi ditampilkan terpisah dan
dihitung saat checkout.

---

## 4. Menambah atau Mengubah Produk

Semua data produk berada di satu tempat, di dalam `index.html` pada blok `PRODUCTS`:

```js
var PRODUCTS = [
  {
    id: 'belanda-irian-jaya',          // unik, dipakai untuk keranjang
    title: 'Judul lengkap produk',     // tampil di kartu
    short: 'Judul ringkas',            // tampil di keranjang & notifikasi
    price: 50000,                      // angka saja, tanpa titik
    url: CHECKOUT_URL,                 // tautan checkout khusus produk ini (lihat di bawah)
    img: 'images/produk-1.webp',       // path relatif
    cat: 'Sejarah Kolonial',           // label kategori di modal
    tags: ['terlaris', 'promo'],       // filter: promo / terlaris / baru
    desc: 'Deskripsi produk...'
  }
];
```

Untuk menambahkan produk: salin satu objek, ubah nilainya, lalu simpan sampulnya ke
folder `images/`. Tidak ada perubahan lain yang diperlukan — kartu, filter, dan
keranjang menyesuaikan otomatis.

Untuk mengubah **tautan pembelian tiap produk**, ubah nilai `url` pada objek produk
yang bersangkutan:

```js
var CHECKOUT_BELANDA_IRIAN_JAYA = 'https://tokopapuaonline.orderhero.id/form/checkout-belanda-irian-jaya';
```

**Saat ini kedua produk memakai `CHECKOUT_BELANDA_IRIAN_JAYA`** karena produk ke-2 belum
memiliki halaman checkout sendiri.

Bila sebuah produk belum diisi `url`, tombol Beli otomatis memakai tautan cadangan
`CHECKOUT_URL`:

```js
var CHECKOUT_URL = 'https://tokopapuaonline.orderhero.id/store';
```

Tautan cadangan ini juga dipakai oleh tombol **"Lanjut ke Pembelian"** di dalam panel
keranjang, bukan oleh tombol Beli pada kartu produk.

---

## 5. Menjalankan Secara Lokal

Halaman dapat dibuka langsung dengan klik ganda pada `index.html`. Bila ingin
memeriksanya lewat server lokal:

```bash
python3 -m http.server 8000
```

lalu buka `http://localhost:8000`.

---

## 6. Spesifikasi Teknis

| Aspek | Nilai |
|---|---|
| Format | Satu berkas HTML (HTML5) |
| CSS | Ditulis langsung, variabel CSS kustom, mobile-first |
| JavaScript | Vanilla ES5-safe, tanpa kerangka kerja |
| Ikon | Inline SVG sprite |
| Font | System font stack (`-apple-system`, `system-ui`, `Segoe UI`, `Roboto`) |
| Warna utama | Teal `#35a8b1` |
| Warna teks | `#111827` |
| Warna garis | `#e5e7eb` |
| Warna footer | `#0e1416` |
| Titik henti | 768 px dan 1100 px |
| Bahasa | `lang="id"` |

---

## 7. Langkah Selanjutnya — Panduan Upload Lengkap

Panduan upload ke GitHub Pages yang **sangat rinci** ada di **`panduan-upload-github.md`**.
Isinya 9 bagian:

| Bagian | Isi |
|---|---|
| 1 | **Persiapan & ekstrak ZIP** — cara ekstrak di Windows / macOS / Android, struktur folder yang benar, cara memastikan `.nojekyll` tidak hilang |
| 2 | **Akun GitHub & repositori** — daftar akun, nama repo yang disarankan, wajib **Public**, jangan centang README/.gitignore/license |
| 3 | **Upload berkas** — (a) lewat web GitHub: *Add file ▾ → Upload files*, drag & drop isi folder + memastikan folder `images/` ikut; (b) lewat **GitHub Desktop**: install → sign in → add local repository → publish → push |
| 4 | **Commit & periksa hasil** — memastikan 9 berkas + folder `images/` tampil di repositori |
| 5 | **Aktifkan GitHub Pages** — *Settings → Pages → Source: Deploy from a branch → Branch `main` → Folder `/ (root)` → Save*, lalu cara menemukan URL situs |
| 6 | **Tunggu & verifikasi situs live** — 1–2 menit, cek gambar tampil, cek tombol **Beli** mengarah ke link checkout, cek tampilan mobile & desktop |
| 7 | **Update di kemudian hari** — edit langsung di GitHub atau unggah ulang, mengganti gambar, menambah produk, memastikan perubahan terbit |
| 8 | **Troubleshooting lengkap** — 404, gambar tidak muncul, CSS/JS tidak jalan, tampil sebagai kode mentah, `.nojekyll` hilang, repo Private, salah folder root, cache browser, mode incognito |
| 9 | **FAQ & daftar periksa** — pertanyaan umum + checklist langkah demi langkah |

### Ringkasan alur upload

1. Ekstrak ZIP ke sebuah folder.
2. Buat repositori GitHub baru berstatus **Public** (kosong, tanpa README).
3. **Add file ▾ → Upload files** → seret seluruh **isi** folder → **Commit changes**.
4. **Settings → Pages** → *Deploy from a branch* → Branch `main` → Folder `/ (root)` → **Save**.
5. Tunggu 1–2 menit, situs aktif di `https://<username>.github.io/<nama-repo>/`.

> **Paling sering salah:** pastikan `index.html` berada di tingkat paling atas repositori
> (sejajar dengan folder `images/`), bukan di dalam subfolder.
