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
| `sitemap.xml` | Daftar URL situs untuk Google — **wajib diganti domainnya** (lihat bagian *SEO*) |
| `robots.txt` | Izin crawler + penunjuk lokasi sitemap — **wajib diganti domainnya** (lihat bagian *SEO*) |
| `CNAME` | **Tidak disertakan** — hanya dibuat kalau sudah punya domain kustom (lihat bagian *Domain Kustom*) |

> **Catatan `CNAME`:** file ini **belum dibuat** karena belum ada domain kustom. Situs akan memakai alamat bawaan GitHub Pages (`https://<username>.github.io/<nama-repo>/`). Cara menambahkannya nanti ada di bagian *Domain Kustom* di bawah.

---

## 🧩 Spesifikasi Landing Page

- **Nama toko:** Toko Papua Online
- **Judul produk:** Laporan Resmi Tindak Kekerasan di Papua (Gugus Tugas UGM)
- **Isi produk:** 135+ halaman PDF · 348 kasus kekerasan (Januari 2010 – Maret 2022) · profil aktor & korban · analisis motif · rekomendasi resmi GTP-UGM
- **Tujuan semua tombol beli:** `https://tokopapuaonline.orderhero.id/landing/laporan-kekerasan-papua`
- **Gambar sampul:** URL absolut dari CDN OrderHero — **tidak perlu upload gambar apa pun**
- **Teknologi:** HTML5 + Tailwind CSS (CDN) + Google Fonts *Plus Jakarta Sans*
- **Tema warna:** slate gelap (`#070B14`) dengan aksen merah (`#DC2626`) dan amber (`#F59E0B`)
- **SEO:** `<link rel="canonical">`, meta `description`, `keywords`, dan `robots` sudah tertanam di `index.html`; dilengkapi `sitemap.xml` + `robots.txt`
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
4. **Drag & drop** seluruh isi paket: `index.html`, `README.md`, `panduan-upload-github.md`, `.nojekyll`, dan folder `images/`.
5. Klik **Commit changes**.
6. Masuk ke **Settings** → menu kiri **Pages**.
7. Pada **Source**, pilih **Deploy from a branch**.
8. Pilih **Branch: `main`** dan **Folder: `/ (root)`** → klik **Save**.
9. Tunggu 1–2 menit, lalu buka `https://<username>.github.io/<nama-repo>/`.

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

### ⚠️ Langkah WAJIB: ganti placeholder domain

`index.html`, `sitemap.xml`, dan `robots.txt` memakai **placeholder** yang harus diganti dengan alamat GitHub Pages Anda yang sebenarnya:

- `USERNAME` → username GitHub Anda
- `NAMA-REPO` → nama repository Anda

Misal username Anda `tokopapua` dan nama repo `landing-laporan-papua`, maka alamat situsnya:
`https://tokopapua.github.io/landing-laporan-papua/`

**Cara 1 — satu perintah di terminal (Linux/macOS/Git Bash):**

```bash
sed -i 's/USERNAME/tokopapua/g; s/NAMA-REPO/landing-laporan-papua/g' index.html sitemap.xml robots.txt
```

**Cara 2 — Windows PowerShell:**

```powershell
foreach ($f in 'index.html','sitemap.xml','robots.txt') {
  (Get-Content $f) -replace 'USERNAME','tokopapua' -replace 'NAMA-REPO','landing-laporan-papua' | Set-Content $f
}
```

**Cara 3 — manual lewat web GitHub:** buka tiap file → klik ikon pensil → ganti `USERNAME` dan `NAMA-REPO` → **Commit changes**.

Setelah diganti, pastikan tiga tempat ini sudah benar:

| File | Yang dicek |
|------|-----------|
| `index.html` | `<link rel="canonical" href="https://…/">` dan `<meta property="og:url" …>` |
| `sitemap.xml` | Baris `<loc>https://…/</loc>` |
| `robots.txt` | Baris `Sitemap: https://…/sitemap.xml` |

> **Punya domain sendiri nanti?** Ganti seluruh URL GitHub Pages di ketiga file itu dengan domain Anda (misal `https://tokopapuaonline.com/`) — jangan menambahkan URL baru, tapi **menggantinya**, agar tidak ada duplikasi.

### Submit Sitemap ke Google Search Console

1. Buka [search.google.com/search-console](https://search.google.com/search-console) → login dengan akun Google.
2. Klik **Add property** → pilih **URL prefix** → masukkan alamat lengkap situs Anda, misal `https://tokopapua.github.io/landing-laporan-papua/` → **Continue**.
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
- **Cek robots.txt:** buka `https://<username>.github.io/<nama-repo>/robots.txt` — pastikan baris `Sitemap:` menunjuk alamat yang benar.
- **Cek sitemap terbaca:** buka `https://<username>.github.io/<nama-repo>/sitemap.xml` — harus tampil sebagai XML yang valid, bukan halaman 404.
- **Lihat performa:** menu **Performance** di Search Console menampilkan kata kunci yang membuat halaman Anda muncul beserta jumlah kliknya.

---

## 🌐 Domain Kustom (Opsional — Nanti)

Belum ada file `CNAME` karena belum ada domain kustom. Kalau nanti Anda punya domain sendiri (misal `tokopapuaonline.com`):

1. Buat file baru bernama **`CNAME`** (tanpa ekstensi) di folder yang sama.
2. Isinya **satu baris saja**: `tokopapuaonline.com`
3. Upload ke repo, lalu buka **Settings → Pages → Custom domain** dan isi nama domain tersebut.
4. Di penyedia domain, arahkan DNS ke GitHub Pages (4 A record untuk domain utama, atau `CNAME` ke `<username>.github.io` untuk subdomain).
5. **Ganti juga domain di `sitemap.xml`, `robots.txt`, dan `<link rel="canonical">` pada `index.html`** menjadi domain baru Anda.
6. Di Google Search Console, tambahkan properti baru untuk domain tersebut dan submit ulang `sitemap.xml`.

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
- [ ] Placeholder `USERNAME` / `NAMA-REPO` sudah diganti di `index.html`, `sitemap.xml`, dan `robots.txt`
- [ ] `sitemap.xml` dan `robots.txt` bisa diakses lewat browser (bukan 404)
- [ ] Sitemap sudah disubmit di Google Search Console

---

© Toko Papua Online. Seluruh hak cipta dilindungi.
