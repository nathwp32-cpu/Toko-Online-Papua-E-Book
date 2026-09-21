# Toko Papua Online — Landing Page E-Book

Landing page statis satu file untuk e-book **"Laporan Resmi Tindak Kekerasan di Papua (Gugus Tugas UGM)"** yang dijual di **Toko Papua Online**.

Paket ini siap diunggah langsung ke GitHub Pages tanpa proses build apa pun.

> **Ingin lebih cepat?** Semua file juga tersedia dalam satu arsip ZIP: `toko-papua-online-paket-github.zip`. Unduh, ekstrak, lalu unggah isinya ke GitHub.

---

## 📁 Isi Folder

| File | Keterangan |
|------|------------|
| `index.html` | **File utama** — seluruh landing page (HTML + Tailwind CSS) dalam satu file |
| `README.md` | Dokumen ini (penjelasan proyek & cara upload) |
| `panduan-upload-github.md` | Panduan langkah demi langkah upload & update di GitHub (Bahasa Indonesia) |
| `.nojekyll` | File kosong, menandai GitHub Pages agar **tidak** memproses situs lewat Jekyll |
| `images/cover.webp` | Gambar sampul e-book (salinan lokal, siap dipakai sebagai cadangan offline) |
| `index-html-source.txt` | Salinan teks dari `index.html` — untuk disalin-tempel bila perlu |
| `sitemap.xml` | Daftar URL situs untuk Google — sudah menunjuk domain `https://tokopapuaonline.com/` |
| `robots.txt` | Izin crawler + penunjuk lokasi sitemap — sudah menunjuk domain kustom |
| `CNAME` | **Sudah disertakan** — berisi `tokopapuaonline.com`. **Jangan dihapus** (lihat bagian *Domain Kustom*) |
| `panduan-setup-dns.md` | Panduan lengkap setup DNS, Custom domain GitHub, HTTPS, dan troubleshooting (Bahasa Indonesia) |

> **Catatan `CNAME`:** file ini sudah berisi `tokopapuaonline.com`, jadi situs siap dilayani di domain kustom tersebut. File ini **wajib tetap ada di root repository** — kalau terhapus, domain akan menampilkan 404. Panduan lengkapnya ada di **`panduan-setup-dns.md`**.

---

## 🧩 Spesifikasi Landing Page

- **Nama toko:** Toko Papua Online
- **Judul produk:** Laporan Resmi Tindak Kekerasan di Papua (Gugus Tugas UGM)
- **Isi produk:** 135+ halaman PDF · 348 kasus kekerasan (Januari 2010 – Maret 2022) · profil aktor & korban · analisis motif · rekomendasi resmi GTP-UGM
- **Tujuan semua tombol beli:** `https://tokopapuaonline.orderhero.id/landing/laporan-kekerasan-papua`
- **Gambar sampul:** URL absolut dari CDN OrderHero — **tidak perlu upload gambar apa pun**
- **Teknologi:** HTML5 + Tailwind CSS (CDN) + Google Fonts *Plus Jakarta Sans*
- **Tema warna:** slate gelap (`#070B14`) dengan aksen merah (`#DC2626`) dan amber (`#F59E0B`)
- **SEO:** `<link rel="canonical">` + meta `description`, `keywords`, `robots`, Open Graph, dan Twitter Card tertanam di `index.html`; dilengkapi `sitemap.xml` + `robots.txt`
- **Schema.org JSON-LD:** blok `application/ld+json` berisi `Organization` + `WebSite` + node gabungan `["Product", "Book"]` untuk e-book, lengkap dengan `offers` harga **Rp 50.000** (lihat bagian *Schema.org JSON-LD*)
- **Domain:** `https://tokopapuaonline.com/` (file `CNAME` sudah disertakan dalam paket)
- **Struktur halaman:**
  1. Navbar sticky
  2. Hero (sampul e-book + statistik + 2 CTA)
  3. Ringkasan isi / poin utama (4 kartu analisis)
  4. Daftar isi (8 bab)
  5. Untuk siapa (6 segmen pembaca)
  6. Harga & CTA pembelian (QRIS)
  7. FAQ (6 pertanyaan, accordion)
  8. Footer + catatan legal
  9. CTA sticky khusus tampilan mobile

---

## 🚀 Cara Upload ke GitHub

### Opsi A — Lewat web GitHub (tanpa terminal, paling mudah)

1. Masuk ke [github.com](https://github.com) → klik **New repository**.
2. Isi nama repo, misal `landing-laporan-papua` → pilih **Public** → **Create repository**.
3. Di halaman repo, klik **Add file** → **Upload files**.
4. **Drag & drop** seluruh isi paket: `index.html`, `README.md`, `panduan-upload-github.md`, `panduan-setup-dns.md`, `sitemap.xml`, `robots.txt`, `.nojekyll`, **`CNAME`**, dan folder `images/`.
5. Klik **Commit changes**.
6. Masuk ke **Settings** → menu kiri **Pages**.
7. Pada **Source**, pilih **Deploy from a branch**.
8. Pilih **Branch: `main`** dan **Folder: `/ (root)`** → klik **Save**.
9. Isi **Custom domain** dengan `tokopapuaonline.com` → **Save** (lihat `panduan-setup-dns.md`), lalu tunggu 1–2 menit dan buka `https://tokopapuaonline.com/`.

### Opsi B — Lewat terminal (Git)

```bash
# 1. Masuk ke folder yang berisi index.html
cd path/ke/folder-landing-page

# 2. Inisialisasi repo lokal
git init

# 3. Tambahkan semua file
git add .

# 4. Simpan sebagai commit pertama
git commit -m "Landing page e-book Toko Papua Online"

# 5. Ganti nama branch utama menjadi main
git branch -M main

# 6. Hubungkan ke repository GitHub (ganti sesuai punya Anda)
git remote add origin https://github.com/<username>/<nama-repo>.git

# 7. Kirim ke GitHub
git push -u origin main
```

Setelah itu aktifkan GitHub Pages lewat **Settings → Pages** seperti langkah 6–9 di Opsi A.

Panduan lebih rinci (termasuk cara update file di kemudian hari dan penanganan error) ada di **`panduan-upload-github.md`**.

---

## 🖼️ Jika Gambar Sampul Tidak Muncul

Gambar sampul dimuat langsung dari server OrderHero. Bila suatu saat server tersebut tidak dapat diakses, aturannya ada di dalam `index.html` — tag `<img>` sudah dibekali atribut `onerror` sebagai cadangan:

- **Cadangan 1 (otomatis, sudah terpasang di `index.html`):** `https://cdn.orderhero.id/users/6aaddd7ab5588d42bc164e82/landing/2026/09/19/15df7b009773add1d1a56db1.webp`
- **Cadangan 2 (sudah ikut dalam paket):** file `images/cover.webp` tersedia di folder yang sama. Kalau ingin tampilan sepenuhnya offline, ubah `src` pada tag `<img>` di dalam `index.html` menjadi `images/cover.webp`.

---

## 🔎 SEO — Sitemap, robots.txt & Google Search Console

Paket ini sudah menyertakan `sitemap.xml` dan `robots.txt`, plus tag SEO dasar di dalam `index.html` (canonical, description, keywords, robots, Open Graph, dan Twitter Card).

### ✅ Domain sudah dikonfigurasi — tidak ada placeholder lagi

Paket ini sudah diatur untuk domain kustom **`https://tokopapuaonline.com/`**. Placeholder `USERNAME` / `NAMA-REPO` **sudah diganti semua** di ketiga file:

| File | Nilai yang tertanam |
|------|---------------------|
| `index.html` | `<link rel="canonical" href="https://tokopapuaonline.com/">` dan `<meta property="og:url" content="https://tokopapuaonline.com/">` |
| `sitemap.xml` | `<loc>https://tokopapuaonline.com/</loc>` |
| `robots.txt` | `Sitemap: https://tokopapuaonline.com/sitemap.xml` |
| `CNAME` | `tokopapuaonline.com` |

**Cara memastikan tidak ada sisa placeholder** — jalankan di folder yang sama:

```bash
grep -rn "USERNAME\|NAMA-REPO" index.html sitemap.xml robots.txt
# Output yang benar: tidak ada apa-apa
```

> **Kalau nanti domainnya berubah:** ganti seluruh alamat `https://tokopapuaonline.com/` di keempat file itu dengan domain baru — **menggantinya**, bukan menambah URL baru, supaya Google tidak menganggapnya konten ganda. Perintah cepatnya ada di `panduan-setup-dns.md` bagian 8.1.

### Submit Sitemap ke Google Search Console

1. Buka [search.google.com/search-console](https://search.google.com/search-console) → login dengan akun Google.
2. Klik **Add property** → pilih **URL prefix** → masukkan alamat lengkap situs Anda: `https://tokopapuaonline.com/` → **Continue**.
3. **Verifikasi kepemilikan.** Untuk GitHub Pages, cara termudah adalah **HTML tag**:
   - Pilih metode **HTML tag**, salin meta tag yang diberikan Google.
   - Tempelkan di dalam `<head>` pada `index.html` (misal tepat di bawah baris `<meta name="robots" …>`).
   - Commit & tunggu 1–2 menit sampai situs ter-*update*, lalu klik **Verify**.
   - *(Alternatif: pilih metode **HTML file**, unduh file verifikasinya, unggah ke root repository.)*
4. Setelah terverifikasi, buka menu **Sitemaps** di panel kiri.
5. Pada kolom **Add a new sitemap**, isi `sitemap.xml` → klik **Submit**.
6. Status akan muncul sebagai **Success**. Google biasanya memerlukan **beberapa hari hingga 2 minggu** untuk mulai mengindeks.

### Mempercepat & memeriksa hasil indeks

- **Request indexing:** di menu **URL Inspection**, tempel alamat halaman Anda → klik **Request Indexing**. Ini meminta Google merayapi halaman itu lebih cepat dari jadwal normal.
- **Cek robots.txt:** buka `https://tokopapuaonline.com/robots.txt` — pastikan baris `Sitemap:` menunjuk alamat yang benar.
- **Cek sitemap terbaca:** buka `https://tokopapuaonline.com/sitemap.xml` — harus tampil sebagai XML yang valid, bukan halaman 404.
- **Lihat performa:** menu **Performance** di Search Console menampilkan kata kunci yang membuat halaman Anda muncul beserta jumlah kliknya.

### Schema.org JSON-LD & Google Rich Results Test

`index.html` memuat blok `<script type="application/ld+json">` dengan **tiga entitas**:

| Entitas | Isi |
|---------|-----|
| `Organization` | Toko Papua Online — nama, URL, logo/sampul, bahasa, wilayah layanan |
| `WebSite` | Situs + relasi ke Organization sebagai publisher |
| `["Product", "Book"]` | E-book-nya: nama, deskripsi, gambar sampul, URL, brand & publisher **Toko Papua Online**, penulis/penyusun **Gugus Tugas Papua UGM**, `bookFormat` EBook, `inLanguage` id-ID, 135 halaman, cakupan 2010-01/2022-03, **`offers` harga Rp 50.000** (`InStock`), serta `BuyAction` ke halaman checkout |

**✅ `offers` sudah diisi** dengan harga e-book yang benar-benar tertera di halaman checkout OrderHero: **Rp 50.000**. Isi lengkapnya di `index.html`:

```json
"offers": {
  "@type": "Offer",
  "url": "https://tokopapuaonline.orderhero.id/landing/laporan-kekerasan-papua",
  "price": "50000",
  "priceCurrency": "IDR",
  "availability": "https://schema.org/InStock",
  "itemCondition": "https://schema.org/NewCondition",
  "seller": {
    "@type": "Organization",
    "name": "Toko Papua Online",
    "url": "https://tokopapuaonline.com/"
  }
}
```

**Kenapa `50000` dan bukan `52850`?** Di halaman checkout, **Rp 2.850** adalah **Biaya Transaksi**, bukan harga produk. Google meminta harga produk itu sendiri, jadi yang dicantumkan adalah Subtotal — **Rp 50.000**. Memasukkan biaya transaksi akan menampilkan harga yang menyesatkan di hasil pencarian.

**Cara memverifikasi harganya:** buka [halaman checkout](https://tokopapuaonline.orderhero.id/landing/laporan-kekerasan-papua), lalu lihat bagian **Ringkasan Pesanan** — baris produk dan Subtotal sama-sama menampilkan **Rp 50.000** (Total menjadi Rp 52.850 setelah biaya transaksi).

Jika harga produk berubah, perbarui `"price"` di `index.html` (tulis angka saja, tanpa titik/koma: Rp 75.000 → `"75000"`), lalu sinkronkan `index-html-source.txt` dan ZIP paketnya.

**Cara menguji di Google Rich Results Test:**

1. Buka [search.google.com/test/rich-results](https://search.google.com/test/rich-results).
2. Tempel `https://tokopapuaonline.com/` → klik **Test URL** (atau pilih tab **Code** lalu tempel isi `index.html` untuk menguji sebelum upload).
3. Yang diharapkan: **Organization** dan **WebSite** terbaca tanpa error, dan node **Product/Book** terdeteksi lengkap dengan **harga Rp 50.000 (IDR)** serta status ketersediaan **In stock** — tanda `offers` sudah dibaca Google dengan benar.
4. Validasi struktur schema.org-nya di [validator.schema.org](https://validator.schema.org) — di sini blok JSON-LD harus lolos tanpa error.

---

## 🌐 Domain Kustom — `tokopapuaonline.com` (Sudah Disiapkan)

Semua file sudah dikonfigurasi untuk domain kustom ini. File **`CNAME`** sudah ada di dalam paket dan berisi satu baris: `tokopapuaonline.com`.

### Yang perlu Anda lakukan

| # | Langkah | Di mana |
|---|---------|---------|
| 1 | Buat **4 A record** `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` | Dashboard DNS registrar |
| 2 | Buat **1 CNAME** `www` → `<username>.github.io` | Dashboard DNS registrar |
| 3 | Isi **Settings → Pages → Custom domain** dengan `tokopapuaonline.com` → **Save** | Repository GitHub |
| 4 | Centang **Enforce HTTPS** setelah sertifikat terbit | Repository GitHub |
| 5 | Tambahkan properti baru `https://tokopapuaonline.com/` di Search Console dan submit `sitemap.xml` | Google Search Console |

**Panduan rinci langkah demi langkah — termasuk tabel record DNS, verifikasi `nslookup`/`dig`, estimasi waktu propagasi, dan troubleshooting lengkap — ada di file `panduan-setup-dns.md`.**

### ⚠️ Jangan hapus file `CNAME`

File `CNAME` adalah satu-satunya penanda yang memberi tahu GitHub Pages bahwa situs Anda dilayani di `tokopapuaonline.com`. Tanpa file itu, domain akan menampilkan **404**. Jangan mengubah namanya, jangan memindahkannya ke sub-folder, dan pastikan isinya tetap satu baris: `tokopapuaonline.com`.

> Kalau `CNAME` terlanjur terhapus: buat file baru bernama `CNAME` di root repository, isi dengan `tokopapuaonline.com`, lalu **Commit changes**. Situs akan pulih dalam 1–2 menit.

---

## 🔄 Cara Update di Kemudian Hari

**Lewat web:** buka `index.html` di repo → klik ikon pensil → edit → **Commit changes**. Situs akan ter-*update* otomatis dalam 1–2 menit.

**Lewat terminal:**

```bash
git add .
git commit -m "Update: perbaikan teks hero"
git push
```

---

## ✅ Checklist Sebelum Publish

- [ ] `index.html` ada di **root** repository (bukan di dalam sub-folder)
- [ ] Nama file persis `index.html` (huruf kecil semua)
- [ ] File `.nojekyll` ikut terunggah
- [ ] Branch **`main`** dan folder **`/ (root)`** sudah dipilih di Settings → Pages
- [ ] Semua tombol beli mengarah ke `https://tokopapuaonline.orderhero.id/landing/laporan-kekerasan-papua`
- [ ] Sampul e-book tampil di bagian hero
- [ ] Tampilan sudah dicek di layar HP dan laptop
- [ ] File **`CNAME`** ada di root repository dan berisi `tokopapuaonline.com`
- [ ] DNS domain sudah diarahkan ke GitHub (4 A record + CNAME `www`) — panduan di `panduan-setup-dns.md`
- [ ] **Settings → Pages → Custom domain** = `tokopapuaonline.com` dan **Enforce HTTPS** sudah dicentang
- [ ] Tidak ada sisa placeholder `USERNAME` / `NAMA-REPO` di `index.html`, `sitemap.xml`, `robots.txt`
- [ ] `https://tokopapuaonline.com/` bisa dibuka dan tampil gembok aman 🔒
- [ ] `sitemap.xml` dan `robots.txt` bisa diakses lewat browser (bukan 404)
- [ ] Sitemap sudah disubmit di Google Search Console

---

© Toko Papua Online. Seluruh hak cipta dilindungi.
