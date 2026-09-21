# Panduan Upload Landing Page ke GitHub Pages

Panduan lengkap dalam Bahasa Indonesia untuk mengunggah landing page **Toko Papua Online** ke GitHub, lalu mengaktifkannya sebagai situs web yang bisa diakses publik.

Tidak perlu bisa programming. Ikuti saja urutannya.

> **Alternatif cepat:** kalau Anda punya arsip `toko-papua-online-paket-github.zip`, ekstrak dulu — semua file (termasuk `.nojekyll` dan folder `images/`) sudah ada di dalamnya.

---

## 📋 Daftar Isi

1. [Persiapan Awal](#1-persiapan-awal)
2. [Membuat Repository Baru](#2-membuat-repository-baru)
3. [Upload File Lewat Web GitHub (Drag & Drop)](#3-upload-file-lewat-web-github-drag--drop)
4. [Mengaktifkan GitHub Pages](#4-mengaktifkan-github-pages)
5. [Mengecek Situs Sudah Tampil](#5-mengecek-situs-sudah-tampil)
6. [SEO — Sitemap, Robots & Google Search Console](#6-seo--sitemap-robots--google-search-console)
7. [Cara Update File di Kemudian Hari](#7-cara-update-file-di-kemudian-hari)
8. [Perintah Git untuk Pengguna Terminal](#8-perintah-git-untuk-pengguna-terminal)
9. [Menghubungkan Domain Sendiri (Opsional)](#9-menghubungkan-domain-sendiri-opsional)
10. [Troubleshooting — Kalau Ada Masalah](#10-troubleshooting--kalau-ada-masalah)

---

## 1. Persiapan Awal

### Yang perlu Anda siapkan

| Kebutuhan | Keterangan |
|-----------|------------|
| **Akun GitHub** | Gratis. Daftar di [github.com/signup](https://github.com/signup) kalau belum punya |
| **File landing page** | `index.html`, `README.md`, `panduan-upload-github.md`, `sitemap.xml`, `robots.txt`, `.nojekyll`, dan folder `images/` (berisi `cover.webp`) |
| **Browser** | Chrome, Firefox, Edge, atau Safari (terbaru) |
| **Koneksi internet** | Stabil, terutama saat upload |

### Susun file di satu folder

Buat satu folder di komputer, misal `landing-laporan-papua`, lalu letakkan semua file itu di dalamnya (sejajar, bukan di dalam sub-folder tambahan):

```
landing-laporan-papua/
├── index.html                  ← file utama, wajib ada
├── README.md
├── panduan-upload-github.md
├── sitemap.xml                 ← daftar URL untuk Google (ganti placeholder-nya!)
├── robots.txt                  ← izin crawler + penunjuk sitemap (ganti placeholder-nya!)
├── .nojekyll
└── images/
    └── cover.webp              ← sampul e-book (cadangan offline)
```

> **Penting:** nama file harus persis `index.html` dengan huruf kecil semua. GitHub Pages mencari nama itu sebagai halaman pembuka.

### Kenali file `.nojekyll`

File ini **tidak punya isi** — hanya perlu keberadaannya. Fungsinya memberi tahu GitHub Pages agar tidak memproses situs Anda lewat mesin Jekyll, sehingga semua file disajikan apa adanya.

Karena namanya diawali titik, file ini tidak terlihat di File Explorer / Finder secara bawaan:

- **Windows:** di File Explorer, buka tab **View** → centang **Hidden items**
- **macOS:** di Finder, tekan `Cmd + Shift + .` (titik) untuk menampilkan file tersembunyi

Saat upload nanti, cukup **drag & drop** file ini juga seperti file lainnya.

---

## 2. Membuat Repository Baru

1. Login ke [github.com](https://github.com).
2. Klik tombol **+** di kanan atas → pilih **New repository**.
   Bisa juga langsung buka [github.com/new](https://github.com/new).
3. Isi kolom berikut:

| Kolom | Isi dengan |
|-------|-----------|
| **Repository name** | `landing-laporan-papua` (huruf kecil, pakai tanda hubung) |
| **Description** | *(opsional)* Landing page e-book Laporan Resmi Papua — Toko Papua Online |
| **Visibility** | **Public** ✅ |
| **Initialize this repository** | Biarkan **kosong semua** (jangan centang README / .gitignore / license) |

4. Klik **Create repository**.

> **Kenapa harus Public?** GitHub Pages gratis hanya bisa dipakai untuk repository publik. Kalau ingin privasi, perlu akun GitHub Pro.

Setelah dibuat, Anda akan melihat halaman kosong dengan petunjuk `…or push an existing repository`. Abaikan saja, kita akan upload lewat web.

---

## 3. Upload File Lewat Web GitHub (Drag & Drop)

1. Di halaman repository yang baru dibuat, klik tautan **uploading an existing file** di tengah halaman.
   — Atau lewat menu: **Add file** ▾ → **Upload files**.
2. Buka folder `landing-laporan-papua` di komputer Anda.
3. **Seleksi semua file** (termasuk `.nojekyll` dan folder `images/`) lalu **drag & drop** ke area upload di halaman GitHub.
   — Bisa juga klik **choose your files** lalu pilih semuanya.
4. Tunggu sampai semua file selesai termuat (muncul daftar namanya di bawah).
5. Di bagian bawah, pada kolom **Commit changes**, tulis keterangan misal:
   `Upload landing page e-book Toko Papua Online`
6. Klik tombol hijau **Commit changes**.

Selesai. Semua file kini ada di repository Anda.

> **Kalau `.nojekyll` tidak ikut ter-upload:** drag & drop hanya file itu sendirian, atau gunakan cara alternatif di bagian [Troubleshooting](#10-troubleshooting--kalau-ada-masalah).

---

## 4. Mengaktifkan GitHub Pages

Inilah langkah yang membuat repository berubah menjadi situs web yang bisa dibuka siapa saja.

1. Di halaman repository, klik tab **Settings** (kanan atas, ikon gerigi).
2. Di menu samping kiri, gulir ke bawah dan klik **Pages**.
3. Pada bagian **Build and deployment** → **Source**, pilih **Deploy from a branch**.
4. Setelah itu muncul pilihan branch:

   | Pengaturan | Pilih |
   |------------|-------|
   | **Branch** | `main` |
   | **Folder** | `/ (root)` |

5. Klik **Save**.
6. Tunggu **1–2 menit**. Refresh halaman Settings → Pages.
7. Akan muncul kotak hijau berisi alamat situs Anda:

   ```
   https://<username-anda>.github.io/landing-laporan-papua/
   ```

   Contoh kalau username Anda `tokopapuaonline`:
   `https://tokopapuaonline.github.io/landing-laporan-papua/`

> **Catatan:** pemilihan folder **`/ (root)`** itu penting, karena `index.html` kita ada di root, bukan di dalam folder `/docs`.

---

## 5. Mengecek Situs Sudah Tampil

1. Buka alamat `https://<username>.github.io/<nama-repo>/` di browser.
2. Lakukan pemeriksaan singkat:
   - [ ] Nama **Toko Papua Online** tampil di navbar kiri atas
   - [ ] Gambar sampul e-book muncul di bagian hero (bukan ikon gambar rusak)
   - [ ] Angka **348** dan **135+** terlihat di kolom statistik
   - [ ] Klik tombol **"Dapatkan E-Book — QRIS Otomatis"** → harus membuka halaman OrderHero di tab baru
   - [ ] Halaman FAQ bisa dibuka-tutup saat diklik
   - [ ] Footer menampilkan **Toko Papua Online**
3. Coba buka juga dari HP untuk memastikan tampilan mobile-nya rapi (akan muncul tombol **Beli Sekarang** menempel di bawah layar).

### Alamat khusus: `username.github.io`

Kalau Anda ingin alamat yang lebih pendek **tanpa nama repo di belakang**, beri nama repository-nya persis seperti ini:

```
<username-anda>.github.io
```

Contoh: username `tokopapuaonline` → nama repo `tokopapuaonline.github.io` → situs bisa dibuka di `https://tokopapuaonline.github.io/`.

Repository jenis ini hanya boleh **satu** per akun.

---

## 6. SEO — Sitemap, Robots & Google Search Console

Landing page ini sudah dibekali perangkat SEO dasar supaya bisa ditemukan Google:

| File | Fungsi |
|------|--------|
| `sitemap.xml` | Daftar URL situs Anda — inilah yang dibaca Google untuk menemukan halaman |
| `robots.txt` | Memberi izin kepada crawler dan menunjuk lokasi sitemap |
| `index.html` | Sudah memuat `<link rel="canonical">`, meta `description`, `keywords`, `robots`, Open Graph, dan Twitter Card |

### ⚠️ Langkah WAJIB — ganti placeholder domain

`sitemap.xml`, `robots.txt`, dan `index.html` masih memakai placeholder. Ganti lebih dulu:

- `USERNAME` → username GitHub Anda
- `NAMA-REPO` → nama repository Anda

Contoh: username `tokopapua` + repo `landing-laporan-papua` → `https://tokopapua.github.io/landing-laporan-papua/`

**Cara cepat — satu perintah (Linux/macOS/Git Bash), dijalankan di folder yang sama:**

```bash
sed -i 's/USERNAME/tokopapua/g; s/NAMA-REPO/landing-laporan-papua/g' index.html sitemap.xml robots.txt
```

**Windows PowerShell:**

```powershell
foreach ($f in 'index.html','sitemap.xml','robots.txt') {
  (Get-Content $f) -replace 'USERNAME','tokopapua' -replace 'NAMA-REPO','landing-laporan-papua' | Set-Content $f
}
```

**Cara manual lewat web GitHub:** buka tiap file → klik ikon pensil ✏️ → ganti `USERNAME` dan `NAMA-REPO` → **Commit changes**.

Setelah diganti, pastikan tiga tempat ini sudah benar:

| File | Yang harus dicek |
|------|------------------|
| `index.html` | `<link rel="canonical" href="https://…/">` dan `<meta property="og:url" …>` |
| `sitemap.xml` | Baris `<loc>https://…/</loc>` |
| `robots.txt` | Baris `Sitemap: https://…/sitemap.xml` |

> **Sudah punya domain sendiri?** Ganti seluruh URL GitHub Pages di ketiga file itu dengan domain Anda — **menggantinya**, bukan menambah URL baru, supaya Google tidak menganggapnya konten ganda.

### Submit sitemap ke Google Search Console

1. Buka [search.google.com/search-console](https://search.google.com/search-console), login dengan akun Google.
2. Klik **Add property** → pilih **URL prefix** → isi alamat situs Anda, misal `https://tokopapua.github.io/landing-laporan-papua/` → **Continue**.
3. **Verifikasi kepemilikan.** Untuk GitHub Pages, cara termudah adalah **HTML tag**:
   - Pilih metode **HTML tag**, lalu salin meta tag yang diberikan Google.
   - Tempelkan di dalam `<head>` pada `index.html` (misal tepat di bawah baris `<meta name="robots" …>`).
   - Commit, tunggu 1–2 menit sampai situs ter-*update*, lalu klik **Verify**.
   - *Alternatif:* pilih metode **HTML file**, unduh file verifikasinya, lalu unggah ke root repository.
4. Setelah terverifikasi, buka menu **Sitemaps** di panel kiri.
5. Di kolom **Add a new sitemap**, isi `sitemap.xml` → klik **Submit**.
6. Status akan muncul sebagai **Success**. Google biasanya butuh **beberapa hari sampai 2 minggu** untuk mulai mengindeks.

### Mempercepat & memantau hasil indeks

- **Request indexing:** buka menu **URL Inspection** → tempel alamat halaman Anda → klik **Request Indexing**.
- **Cek robots.txt:** buka `https://<username>.github.io/<nama-repo>/robots.txt` — baris `Sitemap:` harus menunjuk alamat yang benar.
- **Cek sitemap terbaca:** buka `https://<username>.github.io/<nama-repo>/sitemap.xml` — harus tampil XML yang valid, bukan halaman 404.
- **Pantau performa:** menu **Performance** di Search Console menampilkan kata kunci yang mendatangkan klik.

---

## 7. Cara Update File di Kemudian Hari

### Cara A — Lewat web GitHub (paling cepat untuk perubahan kecil)

1. Buka repository → klik file yang mau diubah, misal `index.html`.
2. Klik ikon **pensil** ✏️ di kanan atas file.
3. Lakukan perubahan.
4. Klik **Commit changes** → tulis keterangan → **Commit changes** lagi.
5. Tunggu 1–2 menit, refresh situs Anda. Perubahan akan langsung tampil.

### Cara B — Ganti file secara utuh

1. Buka repository → klik **Add file** ▾ → **Upload files**.
2. Drag & drop file baru dengan **nama yang sama persis** (`index.html`).
3. **Commit changes** — file lama otomatis tertimpa.

### Cara C — Lewat terminal Git

Lihat [bagian 8](#8-perintah-git-untuk-pengguna-terminal) di bawah.

### Melihat riwayat perubahan

Klik tab **Commits** di repository untuk melihat siapa mengubah apa dan kapan. Kalau ada kesalahan, perubahan bisa dibatalkan lewat tombol **Revert** pada commit terkait.

---

## 8. Perintah Git untuk Pengguna Terminal

Kalau Anda lebih nyaman memakai terminal (Command Prompt, PowerShell, Terminal macOS, atau Git Bash), ikuti langkah ini.

### 8.1 Cek Git sudah terpasang

```bash
git --version
```

Kalau muncul `git version 2.x.x`, berarti siap. Kalau belum ada, unduh di [git-scm.com](https://git-scm.com/downloads).

### 8.2 Inisialisasi repository lokal

Masuk dulu ke folder yang berisi `index.html`:

```bash
cd path/ke/folder/landing-laporan-papua
```

Contoh Windows: `cd C:\Users\Nama\Documents\landing-laporan-papua`
Contoh macOS/Linux: `cd ~/Documents/landing-laporan-papua`

Lalu jalankan berurutan:

```bash
# Inisialisasi Git di folder ini
git init

# Tambahkan semua file (index.html, README.md, panduan-upload-github.md, .nojekyll, images/)
git add .

# Cek file apa saja yang masuk staging area
git status

# Simpan sebagai commit pertama
git commit -m "Landing page e-book Toko Papua Online"

# Pastikan branch utama bernama 'main'
git branch -M main
```

### 8.3 Hubungkan ke GitHub

Buka repository Anda di GitHub, klik tombol hijau **Code**, salin URL-nya (yang berakhiran `.git`), lalu:

```bash
git remote add origin https://github.com/<username>/<nama-repo>.git

# Verifikasi remote sudah benar
git remote -v
```

### 8.4 Kirim ke GitHub

```bash
git push -u origin main
```

Anda akan diminta login. Untuk saat ini GitHub **tidak menerima password akun** — gunakan **Personal Access Token**:

1. Buka [github.com/settings/tokens](https://github.com/settings/tokens)
2. **Generate new token** → **Generate new token (classic)**
3. Beri nama, atur masa berlaku, centang scope **`repo`**
4. Klik **Generate token**, lalu **salin** tokennya (hanya ditampilkan sekali)
5. Saat `git push` meminta password, tempelkan token itu (bukan password akun)

### 8.5 Perintah untuk update berikutnya

```bash
# Lihat perubahan yang terjadi
git status
git diff

# Tambahkan & simpan perubahan
git add .
git commit -m "Update: ganti harga dan perbaikan teks CTA"

# Kirim ke GitHub
git push
```

### 8.6 Perintah bantu yang sering dipakai

```bash
git log --oneline -5        # lihat 5 commit terakhir
git remote -v               # cek alamat remote
git pull                    # ambil perubahan terbaru dari GitHub
git restore index.html      # batalkan perubahan yang belum di-commit
```

### 8.7 Sudah punya repo di GitHub tapi belum punya file lokal

```bash
git clone https://github.com/<username>/<nama-repo>.git
cd <nama-repo>
# copy/paste landing page Anda ke folder ini, lalu:
git add .
git commit -m "Tambah landing page"
git push
```

---

## 9. Menghubungkan Domain Sendiri (Opsional)

Lewat GitHub Pages, situs Anda bisa memakai domain sendiri seperti `tokopapuaonline.com`.

### 9.1 Lewat pengaturan GitHub (disarankan)

1. Buka **Settings** → **Pages**.
2. Di kolom **Custom domain**, isi domain Anda, misal `tokopapuaonline.com` → **Save**.
3. GitHub otomatis membuat file `CNAME` di repository Anda.
4. Di penyedia domain, atur DNS:
   - **Domain utama** (`tokopapuaonline.com`): tambahkan 4 **A record** ke `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - **Subdomain** (`www.tokopapuaonline.com`): tambahkan **CNAME** ke `<username>.github.io`
5. Tunggu propagasi DNS (5 menit – 24 jam), lalu centang **Enforce HTTPS** agar situs aman (https).
6. **Ganti domain di tiga file SEO:** `sitemap.xml`, `robots.txt`, dan `<link rel="canonical">` pada `index.html` — ganti URL GitHub Pages dengan domain baru Anda.
7. Di Google Search Console, klik **Add property** untuk domain baru, verifikasi, lalu submit ulang `sitemap.xml`.

### 9.2 Lewat file `CNAME` manual

Kalau ingin lebih manual, buat file bernama **`CNAME`** (tanpa ekstensi, huruf besar semua) di folder yang sama, isinya satu baris:

```
tokopapuaonline.com
```

Upload ke repo, lalu isi **Custom domain** di Settings → Pages dengan nama yang sama.

> Paket ini **belum menyertakan file `CNAME`** karena Anda belum punya domain kustom. Setelah domainnya ada, baru dibuat.
>
> **Jangan lupa:** setelah domain kustom aktif, perbarui juga `sitemap.xml`, `robots.txt`, dan `<link rel="canonical">` di `index.html` supaya menunjuk domain baru — bukan alamat GitHub Pages lagi.

---

## 10. Troubleshooting — Kalau Ada Masalah

### ❌ Halaman 404 Not Found

**Penyebab paling umum:**

| Penyebab | Solusi |
|----------|--------|
| File tidak bernama `index.html` | Ganti nama jadi persis `index.html` (huruf kecil semua) |
| `index.html` ada di dalam sub-folder | Pindahkan ke **root** repository, atau ubah setelan folder di Pages menjadi `/(root)` |
| Pages belum diaktifkan | Settings → Pages → pilih **Deploy from a branch** → `main` → `/ (root)` → Save |
| Masih menunggu proses build | Tunggu 1–2 menit lalu refresh. Cek tab **Actions** untuk melihat progresnya |
| Salah URL | Pastikan formatnya `https://<username>.github.io/<nama-repo>/` dengan garis miring di akhir |

### ❌ Situs tampil polos tanpa desain (seperti HTML biasa)

Artinya Tailwind CSS dari CDN gagal dimuat. Cek:

1. Apakah koneksi internet aktif?
2. Coba buka di mode incognito — mungkin ada ekstensi browser yang memblokir CDN
3. Cek apakah tag `<script src="https://cdn.tailwindcss.com"></script>` masih ada di dalam `<head>` file `index.html`

### ❌ Gambar sampul e-book tidak muncul

Sampul dimuat dari server OrderHero. Kalau server itu sedang bermasalah, gambar akan gagal tampil.

**Solusi permanen:** unduh sampulnya, simpan sebagai `images/sampul.jpg` di folder yang sama, upload ke repo, lalu ubah bagian `<img src="…">` di dalam `index.html` menjadi:

```html
<img src="images/sampul.jpg" alt="Sampul e-book Laporan Resmi Papua">
```

### ❌ File `.nojekyll` tidak muncul di daftar file

Namanya diawali titik, jadi aplikasi tertentu menyembunyikannya. Cara mengatasinya:

- **Windows:** File Explorer → tab **View** → centang **Hidden items**
- **macOS:** Finder → tekan `Cmd + Shift + .`
- **Alternatif:** buat langsung di GitHub — **Add file** → **Create new file** → tulis nama `.nojekyll` → biarkan isinya kosong → **Commit changes**

Kalau file ini tidak ada, situs biasanya **tetap jalan** — hanya berisiko pada folder yang diawali garis bawah (`_`) yang bisa diabaikan Jekyll.

### ❌ Perubahan tidak muncul setelah di-commit

1. Tunggu 1–2 menit — GitHub Pages punya jeda build.
2. Lakukan **hard refresh**: `Ctrl + F5` (Windows) atau `Cmd + Shift + R` (macOS).
3. Cek tab **Actions** di repository — kalau ada tanda ✗ merah, berarti build gagal; klik untuk melihat penyebabnya.
4. Buka di mode incognito untuk memastikan bukan masalah cache browser.

### ❌ Gagal `git push` karena autentikasi

GitHub tidak lagi menerima password akun untuk operasi Git. Buat **Personal Access Token** (lihat [bagian 8.4](#84-kirim-ke-github)) lalu gunakan token itu sebagai password.

### ❌ Sitemap atau robots.txt error / 404

| Penyebab | Solusi |
|----------|--------|
| File belum diunggah | Unggah `sitemap.xml` dan `robots.txt` ke **root** repository (sejajar `index.html`) |
| Sitemap ditolak Search Console | Pastikan `USERNAME` dan `NAMA-REPO` sudah diganti, dan URL di `<loc>` sama persis dengan alamat situs Anda |
| Data sitemap belum terbaca | Buka `https://<username>.github.io/<nama-repo>/sitemap.xml` di browser — kalau tampil XML, berarti sudah benar |
| Alamat di canonical/`og:url` masih placeholder | Ganti di `index.html`; kalau tidak, Google bisa menganggap alamatnya berbeda |

### ❌ Halaman tidak muncul di Google setelah disubmit

1. Google butuh waktu — biasanya **beberapa hari sampai 2 minggu** untuk indeks pertama.
2. Buka **URL Inspection** di Search Console → tempel alamat halaman → klik **Request Indexing**.
3. Pastikan `robots.txt` **tidak** memblokir, dan meta `robots` di `index.html` berisi `index, follow`.
4. Situs baru sering belum punya tautan masuk; bagikan linknya di media sosial atau grup agar Google menemukannya lebih cepat.

### ❌ Tombol beli tidak membuka halaman OrderHero

Cek di `index.html` apakah tautannya sudah benar:

```
https://tokopapuaonline.orderhero.id/landing/laporan-kekerasan-papua
```

Ganti seluruh tautan lama `https://orderhero.id` dengan alamat di atas, lalu commit ulang.

---

## ✅ Checklist Akhir

- [ ] Repository sudah dibuat dan bersifat **Public**
- [ ] `index.html` ada di **root** repository
- [ ] `.nojekyll`, `README.md`, dan `panduan-upload-github.md` ikut terunggah
- [ ] GitHub Pages aktif: branch **`main`**, folder **`/ (root)`**
- [ ] Situs bisa dibuka di `https://<username>.github.io/<nama-repo>/`
- [ ] Sampul e-book tampil di hero
- [ ] Semua tombol beli mengarah ke halaman OrderHero Toko Papua Online
- [ ] Tampilan sudah dicek di HP dan laptop
- [ ] Placeholder `USERNAME` / `NAMA-REPO` sudah diganti di `index.html`, `sitemap.xml`, dan `robots.txt`
- [ ] `sitemap.xml` dan `robots.txt` bisa dibuka di browser (bukan 404)
- [ ] Sitemap sudah disubmit di Google Search Console dan berstatus **Success**
- [ ] Sudah dibuat catatan: cara update = edit file → **Commit changes**

---

Selamat! Landing page **Toko Papua Online** Anda sudah online dan bisa dibagikan ke calon pembeli.

Kalau nanti ingin menambah halaman atau produk baru, cukup tambahkan file HTML lain di repository yang sama — misalnya `produk-2.html` — dan tautkan dari `index.html`.
