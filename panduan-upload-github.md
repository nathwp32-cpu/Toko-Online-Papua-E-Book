# Panduan Upload ke GitHub Pages — Toko Papua Online

Panduan ini menjelaskan **langkah demi langkah, sangat rinci**, cara menerbitkan halaman
toko **Toko Papua Online** dari paket ZIP ini ke GitHub Pages hingga situsnya aktif dan
dapat dibuka publik.

Hasil akhir: halaman toko aktif pada alamat
`https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/`

**Perkiraan waktu:** 5–10 menit untuk pengguna baru, 3–5 menit bila sudah punya akun GitHub.
**Tingkat kesulitan:** Pemula — tidak perlu pengetahuan pemrograman, tidak perlu Git,
tidak perlu menjalankan perintah terminal (metode A sepenuhnya klik-klik di browser).

---

## Daftar Isi

- [Ringkasan Alur](#ringkasan-alur)
- [Bagian 1 — Persiapan: Ekstrak Paket ZIP](#bagian-1--persiapan-ekstrak-paket-zip)
- [Bagian 2 — Akun GitHub & Membuat Repositori](#bagian-2--akun-github--membuat-repositori)
- [Bagian 3 — Upload Berkas ke Repositori](#bagian-3--upload-berkas-ke-repositori)
- [Bagian 4 — Commit & Periksa Hasil Upload](#bagian-4--commit--periksa-hasil-upload)
- [Bagian 5 — Aktifkan GitHub Pages](#bagian-5--aktifkan-github-pages)
- [Bagian 6 — Tunggu & Verifikasi Situs Live](#bagian-6--tunggu--verifikasi-situs-live)
- [Bagian 7 — Memperbarui Situs di Kemudian Hari](#bagian-7--memperbarui-situs-di-kemudian-hari)
- [Bagian 8 — Pemecahan Masalah (Troubleshooting)](#bagian-8--pemecahan-masalah-troubleshooting)
- [Bagian 9 — FAQ & Daftar Periksa](#bagian-9--faq--daftar-periksa)

---

## Ringkasan Alur

| Langkah | Yang dilakukan | Bagian |
|---|---|---|
| 1 | Unduh & ekstrak paket ZIP | [Bagian 1](#bagian-1--persiapan-ekstrak-paket-zip) |
| 2 | Buat akun/masuk ke GitHub, lalu buat repositori **Public** | [Bagian 2](#bagian-2--akun-github--membuat-repositori) |
| 3 | Unggah seluruh berkas paket ke repositori | [Bagian 3](#bagian-3--upload-berkas-ke-repositori) |
| 4 | Commit & pastikan semua berkas tampil | [Bagian 4](#bagian-4--commit--periksa-hasil-upload) |
| 5 | Aktifkan GitHub Pages (branch `main`, folder `/ (root)`) | [Bagian 5](#bagian-5--aktifkan-github-pages) |
| 6 | Tunggu 1–2 menit, buka situs, verifikasi | [Bagian 6](#bagian-6--tunggu--verifikasi-situs-live) |
| 7 | Periksa `robots.txt` & `sitemap.xml` (alamat sudah terisi, siap pakai) | [Bagian 6.6](#66-memverifikasi-robotstxt--sitemapxml) |
| 8 | Uji tombol **Bagikan** pada kartu produk (WhatsApp, Facebook, X, Telegram, salin tautan) | [Bagian 6.7](#67-memverifikasi-tombol-bagikan-share) |

> **Inti yang paling sering salah:** pastikan berkas `index.html` berada **di tingkat paling
> atas** repositori (sejajar dengan folder `images/`), **bukan** di dalam subfolder. Ini
> penyebab nomor satu situs menampilkan halaman 404 atau tampil tanpa gambar.

---

## Bagian 1 — Persiapan: Ekstrak Paket ZIP

### 1.1 Isi paket

Paket ZIP bernama **`toko-papua-online-store-paket-github.zip`** berisi **11 berkas**:

| # | Berkas | Keterangan | Ukuran |
|---|---|---|---|
| 1 | `index.html` | Halaman toko utama (mobile + desktop, satu berkas) — termasuk tombol **Beli** dan tombol **Bagikan** pada setiap kartu produk | ± 62 KB |
| 2 | `README.md` | Ringkasan proyek | ± 11 KB |
| 3 | `panduan-upload-github.md` | Berkas panduan ini | ± 58 KB |
| 4 | `.nojekyll` | Berkas kosong (0 byte) penanda untuk GitHub Pages | 0 byte |
| 5 | `images/logo.webp` | Logo toko (header & footer) | ± 112 KB |
| 6 | `images/banner-1.webp` | Banner promo carousel 1 | ± 44 KB |
| 7 | `images/banner-2.webp` | Banner promo carousel 2 | ± 97 KB |
| 8 | `images/produk-1.webp` | Sampul produk 1 | ± 95 KB |
| 9 | `images/produk-2.webp` | Sampul produk 2 | ± 34 KB |
| 10 | `robots.txt` | Aturan crawler + baris `Sitemap:` menunjuk ke `sitemap.xml` | ± 1,5 KB |
| 11 | `sitemap.xml` | Peta situs (Sitemap 0.9, UTF-8) berisi URL halaman toko | ± 1,6 KB |

### 1.2 Ekstrak di Windows

**Cara A — File Explorer (paling mudah):**

1. Buka **File Explorer** dan cari berkas `toko-papua-online-store-paket-github.zip`
   (biasanya di folder **Downloads**).
2. **Klik kanan** berkas tersebut, lalu pilih **Extract All…**.
   *Jika tidak ada menu "Extract All", pilih **Open with → Windows Explorer** atau
   **Open with → 7-Zip → Extract Here**.*
3. Pada jendela yang muncul, kolom tujuan akan menampilkan sesuatu seperti
   `C:\Users\NamaAnda\Downloads\toko-papua-online-store-paket-github`.
   Anda boleh menggantinya ke lokasi yang mudah ditemukan (misalnya **Desktop**), lalu
   klik **Extract**.
4. Setelah selesai, sebuah folder baru akan terbuka. Itulah folder paket Anda.
5. **Cara aman memastikan ekstraksi benar-benar selesai:** di dalam folder hasil ekstrak
   harus ada berkas bernama persis `index.html`. Bila yang terlihat hanyalah *file ZIP
   lain* atau tidak ada `index.html`, berarti Anda masih berada di level yang salah —
   masuk lebih dalam ke folder hasil ekstrak.

**Cara B — 7-Zip (bila ZIP diunduh dalam keadaan rusak/terpotong):**

1. Unduh & pasang 7-Zip (gratis) dari **https://www.7-zip.org**.
2. Klik kanan berkas ZIP → **7-Zip → Extract Here**.
3. 7-Zip akan membuat folder `toko-papua-online-store-paket-github` berisi seluruh berkas.

### 1.3 Ekstrak di macOS

1. Buka **Finder** dan cari `toko-papua-online-store-paket-github.zip`.
2. **Klik dua kali** berkas ZIP tersebut. macOS akan otomatis membuat folder hasil ekstrak
   di lokasi yang sama.
   *Atau:* klik kanan → **Open With → Archive Utility**.
3. Buka folder hasil ekstrak, pastikan di dalamnya terlihat `index.html`, `README.md`,
   `panduan-upload-github.md`, dan folder `images`.
4. **Menampilkan berkas tersembunyi (untuk melihat `.nojekyll`):**
   saat Finder aktif, tekan **Command + Shift + titik (.)** secara bersamaan.
   Berkas yang diawali titik akan muncul. Tekan kombinasi yang sama untuk
   menyembunyikannya kembali.

### 1.4 Ekstrak di Android

1. Buka aplikasi **Files by Google** (bawaan Android) atau **ZArchiver** (unduh dari Play Store).
2. Masuk ke folder **Downloads**, ketuk berkas `toko-papua-online-store-paket-github.zip`.
3. **Files by Google:** bila muncul tombol **Extract**, ketuk itu. Bila aplikasi tidak
   mendukung ZIP, pilih **Open with → ZArchiver**.
4. **ZArchiver:** ketuk berkas ZIP → pilih **Extract here** → pilih folder tujuan
   (misalnya `Downloads/tokopapua`) → **OK**.
5. **Menampilkan berkas tersembunyi di ZArchiver:** buka menu (⋮) → **Settings →
   Show hidden files** (atau ikon mata di toolbar), sehingga `.nojekyll` ikut terlihat.

> **Catatan untuk Android:** mengunggah berkas lewat browser di HP bisa dilakukan, tetapi
> proses menyeret (drag & drop) folder `images/` lebih nyaman di komputer. Bila hanya
> tersedia HP, gunakan **Metode A** di [Bagian 3](#bagian-3--upload-berkas-ke-repositori) —
> GitHub Desktop tidak tersedia di Android.

### 1.5 Struktur folder yang benar

Setelah diekstrak, struktur folder **harus seperti ini**:

```
toko-papua-online-store-paket-github/     <- nama folder bisa berbeda, tidak masalah
├── index.html                            <- HARUS di level paling atas
├── README.md
├── panduan-upload-github.md
├── robots.txt
├── sitemap.xml
├── .nojekyll                             <- berkas tersembunyi, 0 byte
└── images/                               <- HARUS sejajar dengan index.html
    ├── logo.webp
    ├── banner-1.webp
    ├── banner-2.webp
    ├── produk-1.webp
    └── produk-2.webp
```

**Struktur yang SALAH** (jangan seperti ini):

```
❌ toko-papua-online-store-paket-github/
   └── toko-papua-online-store/            <- ada folder tambahan di tengah
       └── index.html                      <- index.html jadi terlalu dalam
```

> **Mengapa penting?** Halaman toko memanggil gambarnya dengan **jalur relatif**,
> yaitu `images/logo.webp`. Artinya browser mencari folder `images/` tepat di samping
> tempat `index.html` berada. Bila `index.html` berada di dalam subfolder, seluruh
> gambar akan gagal dimuat (ikon gambar rusak).
>
> Saat mengunggah (Bagian 3), yang diunggah adalah **isi** folder ini — bukan folder
> pembungkusnya.

### 1.6 Memastikan berkas `.nojekyll` tidak hilang

**Mengapa berkas ini ada?** `.nojekyll` adalah berkas kosong (0 byte) tanpa ekstensi yang
memberi tahu GitHub Pages agar **tidak** menjalankan pemrosesan Jekyll pada situs Anda.
Berkas ini bersifat **pengaman tambahan**: paket ini murni HTML/CSS/JavaScript statis, jadi
situs tetap tampil baik meski `.nojekyll` tidak ada. Namun menyertakannya adalah praktik
terbaik agar perilaku situs konsisten.

**Kendala umum:** karena namanya diawali titik, banyak sistem operasi dan aplikasi
**menyembunyikan** berkas ini, sehingga ia tidak terlihat saat Anda memilih berkas untuk
diunggah.

**Cara menampilkan & memastikan berkas ini ada:**

| Sistem | Cara menampilkan berkas tersembunyi |
|---|---|
| Windows 11 | File Explorer → **View → Show → Hidden items** (centang) |
| Windows 10 | Tab **View** → centang **Hidden items** |
| macOS | Di Finder tekan **Command + Shift + .** (titik) |
| Android (ZArchiver) | Menu ⋮ → **Settings → Show hidden files** |
| Linux | Terminal: `ls -a` |

**Mengapa ia hilang saat ekstrak?** Beberapa aplikasi arsip di Windows/Android mengabaikan
entri yang diawali titik. Bila setelah ekstrak Anda tidak menemukan `.nojekyll` sama sekali
(meski berkas tersembunyi sudah diaktifkan), **tidak perlu panik** — buat ulang dengan salah
satu cara berikut:

**Cara 1 — Buat ulang di komputer:**

- **Windows (Notepad):** buka Notepad **kosong** → **File → Save As** → pada kolom
  *File name* ketik `".nojekyll"` **dengan tanda kutip** (tanda kutip memaksa Notepad tidak
  menambahkan `.txt`) → pada *Save as type* pilih **All Files** → simpan ke folder paket.
- **macOS/Linux (Terminal):** masuk ke folder paket lalu jalankan
  `touch .nojekyll` (berkas kosong akan dibuat).

**Cara 2 — Buat langsung di GitHub (paling praktis, dilakukan setelah Bagian 3):**

1. Buka halaman repositori Anda di GitHub.
2. Klik **Add file ▾ → Create new file**.
3. Pada kolom nama berkas, ketik: `.nojekyll`
4. **Biarkan isi berkas kosong** (jangan menulis apa pun).
5. Klik **Commit changes…** → **Commit changes**.

**Verifikasi:** setelah diunggah, di halaman utama repositori berkas `.nojekyll` akan
**terlihat** dalam daftar (GitHub menampilkan seluruh berkas, termasuk yang diawali titik).
Bila tidak terlihat di sana, berarti berkas belum terunggah — ulangi Cara 2 di atas.

---

## Bagian 2 — Akun GitHub & Membuat Repositori

### 2.1 Membuat akun GitHub (lewati bila sudah punya)

1. Buka **https://github.com** di browser.
2. Klik tombol **Sign up** di pojok kanan atas.
3. Isi formulir pendaftaran:
   - **Email** — gunakan email aktif (untuk verifikasi).
   - **Password** — minimal 8 karakter, kombinasikan huruf & angka.
   - **Username** — nama unik Anda; **catat ini**, karena akan dipakai di alamat situs
     (alamat situs selalu dimulai dengan username Anda, diikuti `.github.io`). Gunakan
     huruf kecil, angka, dan tanda hubung.
   - **Country/Region** — pilih **Indonesia**.
4. Selesaikan verifikasi (teka-teki gambar atau kode yang dikirim ke email).
5. Buka email dari GitHub, klik tautan verifikasi untuk mengaktifkan akun.
6. Masuk dengan klik **Sign in** dan isi email + password.

> Bila muncul pertanyaan tentang paket langganan, pilih yang **gratis (Free)** saja.
> GitHub Pages untuk repositori **Public** tidak memerlukan biaya.

### 2.2 Membuat repositori baru

1. Setelah masuk, buka **https://github.com/new**
   (atau klik ikon **+** di pojok kanan atas → **New repository**).
2. Isi kolom berikut:

   | Kolom | Nilai yang diisi |
   |---|---|
   | **Repository name** | `toko-papua-online` — *lihat catatan penamaan di bawah* |
   | **Description** (opsional) | `Halaman toko Toko Papua Online` |
   | **Visibility** | pilih **Public** |
   | **Add a README file** | **JANGAN dicentang** |
   | **Add .gitignore** | biarkan **None** |
   | **Choose a license** | biarkan **None** |

3. Klik tombol **Create repository** di bagian bawah.

**Nama repositori yang dipakai paket ini:**

| Nama repo | Alamat situs hasil | Catatan |
|---|---|---|
| `Toko-Online-Papua-E-Book` | `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/` | **Ini yang sudah dipakai** — alamatnya sudah terisi di `robots.txt` & `sitemap.xml` |
| `toko-papua-online` | `https://tokopapuaonline.github.io/toko-papua-online/` | Alternatif — jelas & mudah diingat |
| `store` | `https://tokopapuaonline.github.io/store/` | Alternatif — singkat |

> **Aturan penamaan:** huruf besar, huruf kecil, angka, tanda hubung (`-`), dan titik (`.`)
> diperbolehkan — **tetapi huruf besar/kecil berpengaruh** pada alamat situs
> (`Toko-Online-Papua-E-Book` berbeda dengan `toko-online-papua-e-book`). Hindari spasi dan
> karakter khusus. Nama repo menjadi bagian dari alamat situs Anda.
>
> **Bila Anda memakai nama repo selain `Toko-Online-Papua-E-Book`:** perbarui alamat di
> `robots.txt` dan `sitemap.xml` agar cocok — lihat [Bagian 7.5](#75-memperbarui-robotstxt--sitemapxml).

> **Mengapa Visibility harus Public?** GitHub Pages gratis hanya dapat diterbitkan dari
> repositori **Public**. Pada repositori **Private**, opsi penerbitan situs tidak tersedia
> kecuali Anda berlangganan paket berbayar.

> **Mengapa JANGAN centang "Add a README file"?** Bila dicentang, GitHub akan membuat
> berkas `README.md` bawaan di repositori. Paket ini sudah punya `README.md` sendiri,
> sehingga akan terjadi konflik/berkas ganda saat mengunggah. Biarkan repositori
> benar-benar kosong.

4. Setelah dibuat, Anda akan melihat halaman repositori berisi pesan
   *"Quick setup — if you've done this kind of thing before"* dan beberapa tautan.
   **Biarkan halaman ini terbuka** — Anda akan memakainya di langkah berikutnya.

---

## Bagian 3 — Upload Berkas ke Repositori

Tersedia **dua metode**. Pilih salah satu:

- **Metode A — Lewat situs web GitHub** (disarankan; tanpa instalasi apa pun).
- **Metode B — Lewat GitHub Desktop** (alternatif bila Anda lebih suka aplikasi).

### Metode A — Lewat situs web GitHub (disarankan)

1. Pada halaman repositori yang baru dibuat, klik tautan
   **uploading an existing file** di bagian tengah halaman.
   *Alternatif:* klik tombol **Add file ▾** di kanan atas → **Upload files**.

2. Buka folder hasil ekstrak (dari Bagian 1) di jendela File Explorer / Finder —
   **letakkan jendela ini di samping jendela browser** agar mudah menyeret berkas.

3. **Pilih SELURUH ISI folder** (bukan foldernya):
   - **Windows:** klik di area kosong folder → tekan **Ctrl + A** untuk memilih semua.
   - **macOS:** klik di area kosong folder → tekan **Command + A**.

   Yang harus terpilih: `index.html`, `README.md`, `panduan-upload-github.md`,
   `robots.txt`, `sitemap.xml`, `.nojekyll` (bila terlihat), dan folder **`images`**.

   > **Penting — jangan menyeret folder pembungkusnya.** Yang diseret adalah *isi* folder
   > (berkas-berkas di dalamnya), bukan folder hasil ekstrak itu sendiri. Bila Anda
   > menyeret folder pembungkus, GitHub akan membuat folder tambahan dan `index.html`
   > akan berakhir terlalu dalam → situs 404.

4. **Seret (drag & drop)** semua yang terpilih ke area unggah di halaman GitHub
   (kotak putus-putus bertuliskan *"Drag files here to add them to your repository"*).

5. **Memastikan folder `images/` ikut terunggah** — periksa daftar berkas di bagian bawah
   kotak unggah. Anda harus melihat baris untuk:
   - `index.html`
   - `README.md`
   - `panduan-upload-github.md`
   - `robots.txt`
   - `sitemap.xml`
   - `.nojekyll` *(mungkin tidak muncul — lihat catatan di bawah)*
   - `images/logo.webp`
   - `images/banner-1.webp`
   - `images/banner-2.webp`
   - `images/produk-1.webp`
   - `images/produk-2.webp`

   GitHub menampilkan jalur lengkap berkas di dalam folder (`images/logo.webp`), jadi
   Anda bisa memastikan kelima gambar benar-benar masuk ke folder `images/`, bukan
   tercecer di level atas.

   > **Bila folder `images/` tidak ikut terseret:** seret folder `images` secara terpisah
   > ke area unggah — GitHub akan otomatis mempertahankan struktur foldernya.
   >
   > **Bila `.nojekyll` tidak muncul di daftar:** itu wajar karena berkas diawali titik dan
   > sering tersembunyi. Ada dua pilihan: (a) lewati saja — situs tetap berfungsi; atau
   > (b) tambahkan belakangan lewat **Add file ▾ → Create new file** dengan nama
   > `.nojekyll` dan biarkan kosong (lihat [Bagian 1.6](#16-memastikan-berkas-nojekyll-tidak-hilang)).

6. Tunggu proses unggah selesai. Indikator kemajuan muncul di sebelah nama tiap berkas.
   Jangan menutup halaman sebelum semua berkas selesai (tidak ada lagi ikon berputar).

7. **Di bagian bawah halaman**, pada kotak **Commit changes**:
   - **Commit message** — biarkan bawaan (*"Add files via upload"*) atau tulis
     `Tambah halaman toko Toko Papua Online`.
   - **Extended description** — boleh dikosongkan.
   - Pilih **Commit directly to the `main` branch** (bawaan).

8. Klik tombol hijau **Commit changes**.

9. Tunggu beberapa detik. Anda akan diarahkan ke halaman repositori yang kini berisi
   berkas-berkas Anda. **Lanjutkan ke [Bagian 4](#bagian-4--commit--periksa-hasil-upload)**
   untuk memeriksa hasilnya.

### Metode B — Lewat GitHub Desktop (alternatif)

GitHub Desktop adalah aplikasi resmi GitHub untuk Windows dan macOS. Metode ini berguna
bila Anda ingin mengelola berkas secara lokal dan mendorongnya (push) dengan satu klik.

> **Tidak tersedia untuk Android/iOS.** Untuk perangkat mobile, gunakan Metode A.

**Langkah 1 — Unduh & pasang GitHub Desktop**

1. Buka **https://desktop.github.com**.
2. Klik **Download for Windows** (atau **Download for macOS**).
3. Jalankan berkas pemasang yang terunduh, lalu ikuti petunjuknya sampai selesai.
4. Buka aplikasi **GitHub Desktop**.

**Langkah 2 — Masuk ke akun GitHub**

1. Pada layar sambutan, klik **Sign in to GitHub.com**.
2. Browser akan terbuka; klik **Authorize desktop** (izinkan aplikasi mengakses akun Anda).
3. Kembali ke aplikasi. Isi **Name** dan **Email** bila diminta (± data ini dipakai sebagai
   tanda penulis setiap perubahan), lalu klik **Finish**.

**Langkah 3 — Daftarkan folder paket sebagai repositori lokal**

1. Di menu atas aplikasi, pilih **File → Add local repository…**
2. Klik **Choose…**, lalu pilih **folder hasil ekstrak** dari Bagian 1
   (folder yang berisi `index.html`).
3. GitHub Desktop akan memberi tahu bahwa folder ini *"is not a Git repository"*.
   Klik tautan **create a repository** yang muncul di pesan tersebut.
4. Pada jendela pembuatan repositori:
   - **Name** — biarkan terisi otomatis (`toko-papua-online-store-paket-github`) atau ubah
     menjadi `toko-papua-online`.
   - **Description** — opsional.
   - **Local path** — biarkan.
   - **Initialize this repository with a README** — **JANGAN dicentang** (paket ini sudah
     punya README sendiri).
   - **Git ignore** — biarkan **None**.
   - **License** — biarkan **None**.
5. Klik **Create repository**.

**Langkah 4 — Terbitkan (publish) ke GitHub**

1. Di bagian atas jendela akan muncul tombol **Publish repository**.
   Klik tombol tersebut.
2. Pada jendela yang muncul:
   - **Name** — misalnya `toko-papua-online` (nama ini akan menjadi nama repo di GitHub).
   - **Description** — opsional.
   - **Keep this code private** — **HILANGKAN centangnya** agar repositori menjadi
     **Public** (syarat GitHub Pages gratis).
   - **Organization** — biarkan **None**.
3. Klik **Publish repository**.
4. Tunggu hingga proses unggah selesai. Setelah selesai, klik
   **Repository → View on GitHub** untuk membuka repositori di browser dan
   memastikan seluruh berkas sudah ada.

**Langkah 5 — Mengubah & mendorong perubahan (push) di kemudian hari**

1. Buka folder paket di File Explorer / Finder, ubah atau tambahkan berkas.
2. Kembali ke GitHub Desktop — perubahan akan langsung terdeteksi dan terdaftar di panel
   kiri **Changes**.
3. Di kotak **Summary** (kiri bawah), tulis ringkasan perubahan, misalnya
   `Perbarui harga produk`.
4. Klik **Commit to main**.
5. Klik **Push origin** di bar atas untuk mengirim perubahan ke GitHub.
6. Tunggu 1–2 menit, lalu muat ulang situs Anda.

---

## Bagian 4 — Commit & Periksa Hasil Upload

Setelah melakukan commit (Metode A langkah 8, atau Metode B langkah 4), Anda akan berada
di halaman utama repositori. Periksa hal-hal berikut:

### 4.1 Daftar berkas di halaman repositori

Halaman repositori harus menampilkan daftar seperti ini (urutan bisa berbeda):

| Nama di daftar | Tipe |
|---|---|
| `images` | Folder |
| `.nojekyll` | Berkas |
| `README.md` | Berkas |
| `index.html` | Berkas |
| `panduan-upload-github.md` | Berkas |
| `robots.txt` | Berkas |
| `sitemap.xml` | Berkas |

Klik folder **`images`** untuk memastikan kelima gambar ada di dalamnya:
`logo.webp`, `banner-1.webp`, `banner-2.webp`, `produk-1.webp`, `produk-2.webp`.

### 4.2 Daftar periksa cepat

- [ ] `index.html` terlihat **di halaman utama repositori** (bukan di dalam subfolder).
- [ ] Folder `images` terlihat **sejajar** dengan `index.html`.
- [ ] Di dalam `images/` terdapat **5 gambar** dengan nama yang benar.
- [ ] `README.md` dan `panduan-upload-github.md` ikut terunggah.
- [ ] `robots.txt` dan `sitemap.xml` ikut terunggah (di level paling atas).
- [ ] `.nojekyll` terlihat (bila tidak, lihat [Bagian 1.6](#16-memastikan-berkas-nojekyll-tidak-hilang)).
- [ ] Kolom **branch** di atas daftar berkas menunjukkan **main**.

> **Bila `index.html` berada di dalam subfolder** (misalnya Anda melihat folder
> `toko-papua-online-store-paket-github` lalu baru `index.html` di dalamnya):
> hapus folder tambahan tersebut. Caranya: klik folder itu → klik ikon **⋯ (More)** →
> **Delete directory** → **Commit changes**. Lalu ulangi [Bagian 3](#bagian-3--upload-berkas-ke-repositori)
> dengan menyeret **isi** folder, bukan foldernya.

### 4.3 Melihat riwayat commit (opsional)

Klik tautan jumlah commit (misalnya *"2 commits"*) di bagian atas daftar berkas untuk
melihat riwayat perubahan. Setiap commit memiliki pesan, waktu, dan penulis — berguna
untuk menelusuri perubahan di kemudian hari.

---

## Bagian 5 — Aktifkan GitHub Pages

1. Di halaman repositori, klik tab **Settings** pada deretan menu atas
   (ikon roda gigi ⚙). Bila tidak terlihat, klik ikon **⋯** di ujung kanan deretan menu,
   lalu pilih **Settings**.

2. Pada panel **kiri**, gulir ke bawah hingga menemukan bagian
   **Code and automation**, lalu klik **Pages**.

3. Pada bagian **Build and deployment**:

   | Kolom | Nilai yang dipilih |
   |---|---|
   | **Source** | **Deploy from a branch** (bukan *GitHub Actions*) |
   | **Branch** | **`main`** |
   | **Folder** (dropdown di sebelah branch) | **`/ (root)`** |

   > **Penting:** jangan pilih `/docs`. Paket ini menempatkan `index.html` di akar
   > repositori, jadi folder harus `/ (root)`.

4. Klik tombol **Save**.

5. Setelah menekan **Save**, halaman akan dimuat ulang. Kembali ke
   **Settings → Pages**, lalu **muat ulang (refresh)** halaman tersebut setelah
   beberapa detik. Akan muncul kotak biru berisi:

   > **Your site is live at `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/`**

   Alamat di kotak itulah **URL situs Anda**. Untuk paket ini alamatnya sudah pasti dan sudah
   tertulis di dalam `robots.txt` serta `sitemap.xml`. Klik **Visit site** untuk membukanya,
   atau salin alamatnya.

> **Bila tombol Save tidak muncul atau opsi Pages tidak ada:** pastikan repositori
> berstatus **Public** (lihat [Bagian 2.2](#22-membuat-repositori-baru) dan
> [Bagian 8.6](#86-repositori-private--situs-tidak-dapat-diterbitkan)).

### 5.1 Cara menemukan URL situs Anda

**URL situs paket ini:**

```
https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/
```

Bila Anda memakai nama repositori yang berbeda, alamatnya menyesuaikan pola:
nama akun Anda + `.github.io/` + nama repositori + `/`.

Anda juga dapat melihat URL-nya kapan saja lewat **Settings → Pages**, atau lewat tab
**Actions** → alur *pages-build-deployment* (bagian **deploy**).

---

## Bagian 6 — Tunggu & Verifikasi Situs Live

### 6.1 Menunggu penerbitan

Penerbitan pertama memerlukan **1–2 menit** (kadang hingga 5 menit pada jam sibuk).

1. Tunggu 1–2 menit.
2. Buka URL situs Anda di browser.
3. Bila masih muncul **404**, tunggu 1 menit lagi dan **muat ulang** halaman.

> Anda bisa memantau prosesnya di tab **Actions** repositori: cari alur bernama
> **pages build and deployment**. Bila tanda centang hijau ✅ muncul, penerbitan selesai.
> Bila tanda silang merah ❌, klik alur tersebut untuk melihat pesan kesalahannya
> (lihat [Bagian 8](#bagian-8--pemecahan-masalah-troubleshooting)).

### 6.2 Daftar verifikasi situs live

Buka situs Anda dan periksa satu per satu:

| # | Yang diperiksa | Hasil yang diharapkan |
|---|---|---|
| 1 | **URL terbuka** | Halaman toko tampil, bukan halaman 404 |
| 2 | **Header** | Logo toko tampil di kiri atas + kolom pencarian |
| 3 | **Banner promo** | Gambar banner tampil penuh (tidak ada ikon gambar rusak) |
| 4 | **Logo & semua gambar tampil** | Tidak ada kotak kosong atau ikon gambar rusak |
| 5 | **Grid produk** | 2–4 kartu produk dengan sampul dan harga `Rp 50.000` |
| 6 | **Tombol Beli** | Tombol hijau toska bertuliskan **🛒 Beli** di setiap kartu |
| 7 | **Klik tombol Beli** | Tab baru terbuka mengarah ke halaman checkout |
| 8 | **Footer tampil** | Footer gelap dengan nama toko dan tautan |
| 9 | **Warna & tata letak** | Skema warna teal/hijau toska, teks terbaca, tidak ada elemen bertumpuk |
| 10 | **`robots.txt` terbuka** | `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/robots.txt` tampil sebagai teks |
| 11 | **`sitemap.xml` terbuka** | `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/sitemap.xml` tampil sebagai XML valid |
| 12 | **Tombol Bagikan tampil** | Ikon bagikan muncul di **setiap** kartu produk, tepat di samping tombol Beli |
| 13 | **Klik tombol Bagikan** | Panel muncul dengan 5 pilihan: **WhatsApp, Facebook, X/Twitter, Telegram, Salin tautan** |

### 6.3 Memverifikasi tombol "Beli" mengarah ke link checkout

Ini pemeriksaan terpenting untuk memastikan halaman toko berfungsi sebagai etalase
yang benar-benar bisa menghasilkan penjualan.

1. Buka situs Anda.
2. Klik tombol **🛒 Beli** pada kartu produk **"E-Book Belanda di Irian Jaya:
   Amtenar di Masa Penuh Gejolak 1945-1962 (Pim Schoorl - KITLV)"**.
   - **Hasil yang diharapkan:** sebuah **tab baru** terbuka dengan alamat
     `https://tokopapuaonline.orderhero.id/form/checkout-belanda-irian-jaya`
     (halaman checkout produk tersebut).
3. Klik tombol **🛒 Beli** pada kartu produk **"E-Book Laporan Tindak Kekerasan di
   Papua (Januari 2010 - Maret 2022) - Gugus Tugas UGM"**.
   - **Hasil yang diharapkan:** sebuah **tab baru** terbuka menuju
     `https://tokopapuaonline.orderhero.id/form/checkout-belanda-irian-jaya`
     *(produk ini **belum memiliki halaman checkout tersendiri** — sudah diuji pada
     2026-09-21: `/form/checkout-laporan-tindak-kekerasan-di-papua` dan beberapa
     varian slug lain mengarah ke halaman Not Found — sehingga tombolnya sementara
     diarahkan ke tautan checkout yang tersedia agar tetap berfungsi).*
   - Begitu tautan checkout khusus produk tersebut tersedia, ubah nilai `url` pada
     objek `laporan-kekerasan-papua` di dalam blok `PRODUCTS` — lihat
     [Bagian 7](#7-memperbarui-halaman-di-kemudian-hari).
4. Bila tab baru **tidak** terbuka, atau alamat yang terbuka salah, lihat baris
   *"Tombol Beli tidak berfungsi"* pada
   [Bagian 8.10](#810-tabel-ringkas-masalah--solusi).

### 6.4 Memverifikasi tampilan mobile (HP)

1. Buka situs Anda di HP, **atau** pada browser desktop tekan **F12** untuk membuka
   Developer Tools → klik ikon perangkat (📱) → pilih ukuran layar **iPhone 14 Pro
   (393 × 852)** atau isi manual **390 × 844**.
2. Periksa:
   - Header lebih ringkas (logo + kolom pencarian).
   - **Bottom tab bar** muncul di bagian bawah layar
     (Home / Produk / Keranjang / Lainnya).
   - Grid produk menjadi **2 kolom**.
   - **Tidak ada halaman yang bisa digeser ke kiri/kanan** (tidak ada scroll horizontal).
   - Semua tombol **Beli** dapat ditekan dengan nyaman.

### 6.5 Memverifikasi tampilan desktop (PC)

1. Kembali ke tampilan normal browser (matikan mode perangkat) atau atur ke
   **1280 × 900**.
2. Periksa:
   - **Menu navigasi** (Home / Produk / Tentang) tampil di header.
   - Tombol **keranjang** tampil di kanan header.
   - Grid produk menjadi **3–4 kolom**.
   - **Bottom tab bar tidak tampil** (memang disembunyikan di desktop).
   - **Tidak ada scroll horizontal.**

---

### 6.6 Memverifikasi `robots.txt` & `sitemap.xml`

Dua berkas ini membantu mesin pencari mengenali situs Anda. Keduanya **tidak memengaruhi
tampilan halaman**, tetapi sebaiknya diperiksa sekali setelah situs live.

**A. Alamat situs sudah terisi — tidak ada yang perlu diganti**

Kedua berkas **sudah memuat URL GitHub Pages yang sebenarnya**, jadi paket ini siap diunggah
apa adanya:

| Berkas | Isi alamat |
|---|---|
| `robots.txt` | `Sitemap: https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/sitemap.xml` |
| `sitemap.xml` | `<loc>https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/</loc>` |

Anda **tidak perlu** mengganti apa pun. Langsung lanjut ke langkah B untuk memeriksanya.

**Bila di kemudian hari nama repositori berubah**, perbarui alamat di **kedua** berkas agar
tetap sama persis. Cara mengedit lewat web GitHub: buka berkasnya → klik ikon **pensil**
(*Edit this file*) → ubah teksnya → **Commit changes**. Perhatikan huruf besar/kecil: nama
repositori ini ditulis persis `Toko-Online-Papua-E-Book`.

**B. Buka berkasnya di browser**

1. `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/robots.txt`
   - **Diharapkan:** tampil sebagai teks biasa, memuat baris `User-agent: *`, `Allow: /`,
     dan satu baris `Sitemap:` yang menunjuk ke
     `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/sitemap.xml`.
   - Bila muncul **404**, lihat [Bagian 8.1](#81-situs-menampilkan-halaman-404).
2. `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/sitemap.xml`
   - **Diharapkan:** tampil sebagai XML, dimulai dengan
     `<?xml version="1.0" encoding="UTF-8"?>` dan memuat satu blok `<url>` berisi
     `<loc>https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/</loc>`.
   - Bila browser menampilkan pesan kesalahan XML (*"This page contains the following
     errors"*), berarti ada karakter yang rusak saat menyunting — salin ulang berkasnya dari
     ZIP paket dan pastikan tidak menghapus tanda `<` `>` maupun garis miring.

**C. Memastikan tidak ada kesalahan ketik pada alamat**

- Alamat di `robots.txt` dan di `sitemap.xml` harus **sama persis**.
- Tidak boleh ada sisa tanda `<` atau `>` pada alamat.
- Tidak boleh ada spasi di dalam alamat.
- **Huruf besar/kecil berpengaruh.** Nama repositori ini ditulis persis
  `Toko-Online-Papua-E-Book`; alamat `toko-online-papua-e-book` adalah alamat yang **berbeda**
  dan akan menghasilkan 404.

> **Catatan:** bila situs Anda nanti dipindahkan ke alamat lain, cukup perbarui kedua berkas
> ini — lihat [Bagian 7](#bagian-7--memperbarui-situs-di-kemudian-hari).

---

### 6.7 Memverifikasi tombol Bagikan (Share)

Setiap kartu produk memiliki **tombol Bagikan** (ikon bagikan) di sebelah tombol Beli.
Tombol ini untuk membagikan produk ke media sosial, sehingga pembeli lain bisa menemukan
toko Anda.

**A. Pastikan tombolnya tampil**

1. Buka situs Anda.
2. Lihat setiap kartu produk di grid.
   - **Diharapkan:** di samping tombol hijau toska **🛒 Beli** ada tombol persegi putih
     berisi **ikon bagikan** (tiga titik yang terhubung garis).
   - Tombol ini harus ada di **semua** kartu produk, bukan hanya satu.
3. Periksa juga di HP: kedua tombol tetap sejajar dan tidak saling menumpuk.

**B. Uji panel bagikan**

1. Klik tombol **Bagikan** pada salah satu kartu produk.
2. **Diharapkan:** muncul panel dari bawah layar (di PC: di tengah layar) berisi:
   - Judul panel **"Bagikan produk"**.
   - Nama produk yang dipilih (mis. *E-Book Belanda di Irian Jaya…*).
   - **5 pilihan:** WhatsApp · Facebook · X / Twitter · Telegram · Salin tautan.
3. Cek masing-masing pilihan satu per satu:

| Pilihan | Yang diharapkan saat diklik |
|---|---|
| **WhatsApp** | Tab baru terbuka ke `wa.me` berisi pesan berisi **nama produk + alamat situs** |
| **Facebook** | Tab baru terbuka ke jendela berbagi Facebook dengan tautan halaman situs |
| **X / Twitter** | Tab baru terbuka ke jendela tulis X berisi **nama produk + tautan** |
| **Telegram** | Tab baru terbuka ke `t.me/share` berisi **tautan + nama produk** |
| **Salin tautan** | Tautan tersalin ke papan klip + muncul notifikasi *"Tautan produk disalin"* |

   > Bila tab baru **tidak** terbuka, kemungkinan pemblokir pop-up aktif. Lihat baris
   > *"Tombol Beli tidak berfungsi"* pada [Bagian 8.10](#810-tabel-ringkas-masalah--solusi).

4. **Uji Salin tautan:** klik **Salin tautan** → tempelkan (Ctrl+V / Cmd+V) di kolom
   pesan atau catatan mana pun. Yang tersalin harus berupa
   **nama produk + alamat situs** `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/`.

**C. Pastikan panel bisa ditutup dengan 3 cara**

| Cara | Yang dilakukan |
|---|---|
| Klik di luar | Klik area gelap di sekitar panel |
| Tombol **×** | Klik tombol silang di pojok kanan atas panel |
| Tombol **Esc** | Tekan tombol `Esc` di papan tombol |

Ketiganya harus menutup panel. Setelah panel tertutup, pastikan tombol
**🛒 Beli** tetap berfungsi seperti biasa (buka halaman checkout di tab baru).

---

## Bagian 7 — Memperbarui Situs di Kemudian Hari

Setiap kali Anda mengubah berkas di repositori, GitHub Pages akan **menerbitkan ulang
situs secara otomatis** dalam 1–2 menit.

### 7.1 Mengubah teks / struktur halaman

**Cara A — Edit langsung di GitHub (paling cepat):**

1. Buka repositori Anda di GitHub.
2. Klik berkas yang ingin diubah (misalnya `index.html`).
3. Klik ikon **pensil ✏ (Edit this file)** di kanan atas.
4. Lakukan perubahan (misalnya mengubah harga, judul, atau deskripsi produk).
5. Klik **Commit changes…** di kanan atas.
6. Isi pesan commit, misalnya `Ubah harga produk 1`, lalu klik **Commit changes**.
7. Tunggu 1–2 menit, lalu muat ulang situs Anda.

**Cara B — Unggah ulang dari komputer:**

1. Ubah berkas di komputer Anda.
2. Buka folder yang sesuai di repositori → **Add file ▾ → Upload files** → seret berkas
   dengan **nama yang sama** → **Commit changes**.
   GitHub akan menimpa berkas lama secara otomatis.
3. Untuk mengganti seluruh isi, unggah semua berkas seperti pada
   [Bagian 3](#bagian-3--upload-berkas-ke-repositori).
4. Tunggu 1–2 menit, lalu muat ulang situs.

### 7.2 Mengganti gambar

1. Siapkan gambar baru. **Gunakan nama berkas yang persis sama** dengan gambar lama
   (misalnya `logo.webp`) agar halaman otomatis memakai gambar baru tanpa perlu
   mengubah `index.html`.
2. Buka folder **`images`** di repositori GitHub.
3. Klik **Add file ▾ → Upload files**.
4. Seret gambar baru Anda → **Commit changes**.
5. Tunggu 1–2 menit, lalu muat ulang situs dengan **hard refresh**
   (**Ctrl + Shift + R** di Windows/Linux, **Cmd + Shift + R** di macOS).

> **Format gambar yang didukung:** `.webp`, `.jpg`, `.jpeg`, `.png`, `.gif`.
> Bila Anda memakai nama berkas **berbeda**, Anda juga harus menyesuaikan namanya di
> dalam `index.html` pada blok `PRODUCTS`.

### 7.3 Menambah produk baru

Seluruh data produk berada di satu tempat di dalam `index.html`, pada blok `PRODUCTS`:

```js
var PRODUCTS = [
  {
    id: 'belanda-irian-jaya',          // unik, dipakai untuk keranjang
    title: 'Judul lengkap produk',     // tampil di kartu
    short: 'Judul ringkas',            // tampil di keranjang & notifikasi
    price: 50000,                      // angka saja, tanpa titik
    url: CHECKOUT_URL,                 // tautan checkout khusus produk ini
    img: 'images/produk-1.webp',       // path relatif
    cat: 'Sejarah Kolonial',           // label kategori
    tags: ['terlaris', 'promo'],       // filter: promo / terlaris / baru
    desc: 'Deskripsi produk...'
  }
];
```

**Langkah menambah produk:**

1. Unggah sampul produk baru ke folder `images/` dengan nama sederhana, misalnya
   `produk-3.webp` (huruf kecil, tanpa spasi).
2. Edit `index.html`, salin satu objek di dalam `PRODUCTS`, letakkan di bawahnya,
   lalu ubah seluruh nilainya (terutama `id` harus unik dan `img` menunjuk berkas baru).
3. Simpan / commit perubahan.
4. Tunggu 1–2 menit. Kartu produk baru akan muncul otomatis — filter, pencarian,
   keranjang, **dan tombol Bagikan** menyesuaikan sendiri tanpa perubahan kode lain.

### 7.4 Memastikan perubahan sudah terbit

1. Buka tab **Actions** di repositori.
2. Cari alur terbaru bernama **pages build and deployment**.
3. Pastikan statusnya **✅ hijau** dan selesai (bukan berputar / ⏳).
4. Buka situs Anda dengan **mode incognito** atau **hard refresh** untuk memastikan
   Anda tidak melihat versi lama dari cache browser.
5. Bila perubahan masih belum tampak setelah 5 menit, lihat
   [Bagian 8.8](#88-cache-browser-menampilkan-versi-lama).

### 7.5 Memperbarui `robots.txt` & `sitemap.xml`

Kedua berkas ini juga bisa diubah kapan saja, baik lewat web GitHub maupun dengan
mengunggah ulang.

**Bila Anda mengganti nama repositori**, atau memindahkan situs ke alamat lain, perbarui
alamat di **kedua** berkas (sekarang keduanya sudah terisi alamat paket ini):

| Berkas | Baris yang diubah |
|---|---|
| `robots.txt` | `Sitemap: https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/sitemap.xml` |
| `sitemap.xml` | `<loc>https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/</loc>` |

> Jangan lupa huruf besar/kecilnya harus sama persis di **kedua** berkas.

**Cara lewat web GitHub:**

1. Buka berkasnya di repositori → klik ikon **pensil** (*Edit this file*).
2. Ubah alamatnya.
3. **Commit changes**.
4. Tunggu 1–2 menit, lalu buka kembali alamat berkas itu di browser dan muat ulang.

**Bila Anda menambah halaman baru** (misalnya `tentang.html`), tambahkan satu blok `<url>`
baru di dalam `sitemap.xml`, tepat sebelum baris `</urlset>`:

```xml
  <url>
    <loc>https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/tentang.html</loc>
    <lastmod>2026-09-21</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>
```

> Perbarui juga tanggal `<lastmod>` setiap kali halaman berubah, agar mesin pencari tahu
> isinya baru.

### 7.6 Mengubah teks & tautan pada tombol Bagikan

Tombol Bagikan membagikan **alamat situs + nama produk**. Alamat situs yang dibagikan
diatur pada satu baris di dalam `index.html`:

```js
var PAGE_URL = 'https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/';
```

**Kapan perlu diubah:** bila Anda mengganti **nama repositori** atau memindahkan situs ke
alamat lain. Samakan nilainya dengan alamat situs yang baru (harus diakhiri garis miring `/`).

**Cara mengubahnya lewat web GitHub:**

1. Buka `index.html` di repositori → klik ikon **pensil** (*Edit this file*).
2. Cari baris `var PAGE_URL = ...` (gunakan **Ctrl + F** / **Cmd + F**).
3. Ganti alamatnya, lalu **Commit changes**.
4. Tunggu 1–2 menit, lalu buka situs dengan **hard refresh** dan uji tombol Bagikan.

**Mengubah teks ajakan.** Tepat di bawah baris `PAGE_URL` ada fungsi `shareTextFor` yang
menyusun kalimat yang dikirim ke media sosial:

```js
function shareTextFor(p) {
  if (!p) { return 'Toko Papua Online E-Book\n' + PAGE_URL; }
  return p.title + ' - ' + rupiah(p.price) +
    '\n\nBeli e-book ini di Toko Papua Online:\n' + PAGE_URL;
}
```

Ubah teks `'Beli e-book ini di Toko Papua Online:'` bila ingin kalimat ajakan yang berbeda.
Biarkan bagian `p.title` dan `PAGE_URL` apa adanya agar nama produk dan alamat situs tetap
ikut terbagikan.

**Menambah atau menghapus media sosial.** Kelima pilihan ada di dalam blok
`<div class="share-grid">` pada bagian **SHARE SHEET** di `index.html`. Setiap pilihan
adalah satu elemen `<a class="share-item ...">` (atau `<button>` untuk *Salin tautan*).
Saat mengubahnya, pastikan atribut `id` dan `data-share-go` tidak diubah, karena keduanya
dipakai oleh JavaScript.

> **Catatan:** tombol Bagikan **tidak menambah berkas baru** ke paket. Seluruh ikonnya
> memakai inline SVG sprite yang sudah ada di `index.html`.

---

## Bagian 8 — Pemecahan Masalah (Troubleshooting)

### 8.1 Situs menampilkan halaman 404

**Gejala:** membuka URL situs menampilkan halaman *"404 — There isn't a GitHub Pages site
here"* atau halaman 404 buatan GitHub.

**Penyebab & solusi (periksa berurutan):**

1. **Belum menunggu cukup lama** — penerbitan pertama butuh 1–2 menit (kadang 5 menit).
   Tunggu, lalu muat ulang.
2. **GitHub Pages belum diaktifkan** — buka **Settings → Pages**, pastikan **Source**
   sudah diatur ke **Deploy from a branch** dan sudah menekan **Save** (Bagian 5).
3. **Branch/folder salah** — di **Settings → Pages** pastikan **Branch = `main`** dan
   **Folder = `/ (root)`**. Bila branch yang ada bernama `master`, pilih `master`.
4. **`index.html` berada di dalam subfolder** — buka halaman utama repositori. Bila
   `index.html` tidak terlihat di sana (berada di dalam folder lain), pindahkan ke akar
   repositori (lihat [Bagian 4.2](#42-daftar-periksa-cepat)).
5. **Nama berkas tidak tepat** — berkas utama harus bernama persis `index.html`
   (huruf kecil semua, bukan `Index.html` atau `index.HTML`). Ganti nama bila perlu lewat
   ikon **⋯ → Rename**.
6. **Repo Private** — lihat [Bagian 8.6](#86-repositori-private--situs-tidak-dapat-diterbitkan).
7. **Alamat salah tulis** — paket ini memakai alamat
   `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/`. Pastikan huruf besar/kecilnya
   persis sama dan ada garis miring `/` di akhir.
8. **Alur penerbitan gagal** — buka tab **Actions**, cek apakah *pages build and
   deployment* berstatus ❌. Klik alurnya untuk melihat pesan kesalahan.

### 8.2 Gambar tidak muncul (ikon gambar rusak / kotak kosong)

**Gejala:** halaman tampil, tetapi logo, banner, dan sampul produk tidak muncul;
muncul ikon gambar rusak.

**Penyebab & solusi:**

1. **Folder `images/` tidak ikut terunggah** (penyebab paling umum).
   - Buka halaman utama repositori. Bila tidak ada folder `images`, unggah ulang folder
     tersebut: **Add file ▾ → Upload files** → seret folder `images` → **Commit changes**.
2. **`index.html` berada di dalam subfolder, sedangkan `images/` di akar** (atau
   sebaliknya). Keduanya **harus sejajar**. Perbaiki dengan memindahkan `index.html` ke
   akar (atau menghapus folder pembungkus).
3. **Struktur folder di dalam `images/` terlalu dalam** — pastikan di dalam repositori
   jalurnya persis `images/logo.webp`, **bukan** `images/images/logo.webp`.
   Klik folder `images` di GitHub untuk memeriksanya.
4. **Nama berkas berbeda huruf besar/kecil** — GitHub Pages peka huruf besar-kecil
   (case-sensitive). `Logo.webp` ≠ `logo.webp`. Pastikan nama berkas di repositori
   **persis sama** dengan yang dirujuk di `index.html` (huruf kecil semua).
5. **Nama berkas berubah saat ekstrak** — sebagian aplikasi arsip menambahkan akhiran
   pada nama berkas. Periksa dan ganti nama bila perlu (**⋯ → Rename**).
6. **Berkas gambar rusak saat unggah** — unggah ulang berkas gambar yang bersangkutan
   dari ZIP asli.

**Cara memeriksa cepat:** ketik langsung alamat gambar di browser, misalnya
`https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/images/logo.webp`.
- **Gambar tampil** → berarti gambar ada; masalahnya ada pada jalur di `index.html`
  atau pada cache (lakukan hard refresh).
- **Muncul 404** → berkas gambar memang tidak ada / berada di jalur yang salah di
  repositori; unggah ulang ke folder `images/`.

### 8.3 CSS / JavaScript tidak jalan (halaman tampil polos tanpa gaya)

**Gejala:** teks tampil hitam-putih tanpa tata letak, tombol tidak berfungsi, carousel
banner diam.

**Penyebab & solusi:**

1. **JavaScript dinonaktifkan di browser** — paket ini menggunakan JavaScript untuk
   merender kartu produk, carousel, keranjang, dan modal. Aktifkan JavaScript:
   - **Chrome:** Settings → Privacy and security → Site Settings → JavaScript →
     **Sites can use JavaScript**.
   - **Safari:** Settings → Safari → Advanced → aktifkan **JavaScript**.
   - Bila memakai ekstensi pemblokir script (mis. NoScript), izinkan situs Anda.
2. **Berkas `index.html` tidak lengkap saat diunggah** — berkas ini memuat seluruh CSS
   dan JavaScript **di dalam satu berkas**. Bila unggahan terputus, sebagian isi berkas
   bisa hilang. Perbaikan: buka `index.html` di GitHub, tekan **Ctrl + F** dan cari
   `</html>` di bagian paling akhir. Bila tidak ada, unggah ulang `index.html` dari ZIP.
3. **Cache browser menampilkan versi lama** — lakukan hard refresh
   (**Ctrl + Shift + R** / **Cmd + Shift + R**) atau buka di mode incognito.
4. **Membuka berkas lokal langsung dari ZIP** — jangan menjalankan `index.html` dari
   dalam arsip ZIP (belum diekstrak); ekstrak dulu, atau buka langsung lewat URL situs.

### 8.4 Situs tampil sebagai kode mentah (menampilkan isi berkas, bukan halaman)

**Gejala:** browser menampilkan kode HTML, atau halaman menampilkan isi `README.md`
seolah-olah sebagai halaman utama.

**Penyebab & solusi:**

1. **Berkas utama tidak bernama `index.html`** — GitHub Pages selalu mencari berkas
   `index.html` di akar folder yang dipilih. Bila berkas Anda bernama lain (mis.
   `Index.html`, `home.html`, `toko.html`), ganti namanya:
   klik berkas → ikon **⋯ → Rename** → ketik `index.html` → **Commit changes**.
2. **`index.html` berada di dalam subfolder** — GitHub Pages akan menampilkan daftar
   berkas (bukan halaman) karena tidak menemukan `index.html` di akar. Pindahkan berkas
   ke akar repositori (lihat [Bagian 4.2](#42-daftar-periksa-cepat)).
3. **Folder yang dipilih di Settings → Pages adalah `/docs`** padahal berkas ada di akar
   (atau sebaliknya). Ubah ke **`/ (root)`**.
4. **Anda membuka URL berkas, bukan URL situs** — misalnya membuka
   `.../README.md`. GitHub akan menampilkan isi berkas. Gunakan URL
   `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/` (tanpa nama berkas di akhir).

### 8.5 Berkas `.nojekyll` hilang

**Gejala:** `.nojekyll` tidak terlihat setelah ekstrak, atau tidak ada di repositori.

**Solusi:**

1. **Tidak masalah bila terlewat** — paket ini murni HTML/CSS/JS statis, jadi situs tetap
   berfungsi tanpanya. Berkas ini hanya pengaman tambahan.
2. **Bila ingin menambahkannya:** buka repositori → **Add file ▾ → Create new file** →
   ketik nama `.nojekyll` → **biarkan isi kosong** → **Commit changes…** → **Commit changes**.
3. **Verifikasi:** berkas `.nojekyll` akan muncul di daftar berkas halaman utama
   repositori. Bila sudah ada, jangan diubah.
4. Ikuti [Bagian 1.6](#16-memastikan-berkas-nojekyll-tidak-hilang) untuk cara memastikan
   berkas ini ikut saat ekstrak / unggah.

### 8.6 Repositori Private — situs tidak dapat diterbitkan

**Gejala:** pada **Settings → Pages**, opsi penerbitan tidak tersedia, atau muncul pesan
bahwa GitHub Pages tidak tersedia untuk repositori Private.

**Solusi:**

1. Buka repositori → **Settings**.
2. Gulir ke bawah ke bagian paling bawah halaman (**Danger Zone**).
3. Klik **Change repository visibility** → **Change to public**.
4. Ikuti konfirmasi yang diminta (ketik nama repositori untuk mengonfirmasi).
5. Kembali ke **Settings → Pages** dan ulangi [Bagian 5](#bagian-5--aktifkan-github-pages).

> GitHub Pages gratis hanya tersedia untuk repositori **Public**. Bila isi proyek Anda
> sensitif dan memang harus Private, opsi penerbitan situs memerlukan paket berbayar.

### 8.7 Salah folder root

**Gejala:** sudah diaktifkan tetapi 404, atau halaman menampilkan daftar berkas,
sementara berkas sebenarnya ada di repositori.

**Solusi:** di **Settings → Pages**, kolom **Folder** harus **`/ (root)`** karena
`index.html` berada di akar repositori. Jangan pilih `/docs`. Setelah mengganti, klik
**Save** dan tunggu 1–2 menit.

### 8.8 Cache browser menampilkan versi lama

**Gejala:** Anda sudah mengubah `index.html` di GitHub dan commit berhasil, tetapi situs
masih menampilkan versi lama.

**Solusi (berurutan):**

1. **Tunggu 1–2 menit** — penerbitan otomatis butuh waktu. Cek tab **Actions** untuk
   memastikan alur terbaru sudah ✅.
2. **Hard refresh:**
   - Windows/Linux: **Ctrl + F5** atau **Ctrl + Shift + R**
   - macOS: **Cmd + Shift + R**
   - Android/iOS: tutup tab lalu buka ulang, atau bersihkan cache browser.
3. **Kosongkan cache:**
   - **Chrome/Edge:** Ctrl + Shift + Delete → pilih *Cached images and files* →
     *Clear data*.
   - **Safari (macOS):** Develop → *Empty Caches* (aktifkan menu Develop lebih dulu).
4. **Tambah parameter pada URL** untuk memaksa versi baru, misalnya
   `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/?v=2`.

### 8.9 Cara memeriksa lewat mode incognito

Mode incognito/penyamaran tidak memakai cache browser, sehingga cara tercepat untuk
memastikan apakah masalahnya benar-benar di situs Anda atau hanya cache.

**Cara membuka:**

- **Chrome / Edge (Windows):** **Ctrl + Shift + N**
- **Chrome (macOS):** **Cmd + Shift + N**
- **Firefox (Windows):** **Ctrl + Shift + P**
- **Firefox (macOS):** **Cmd + Shift + P**
- **Safari (macOS):** **File → New Private Window** (Cmd + Shift + N)
- **Android:** Chrome → menu ⋮ → **New Incognito tab**
- **iOS:** Safari → ikon tab → **Private** → **+**

**Cara membaca hasilnya:**

| Hasil di incognito | Artinya | Tindakan |
|---|---|---|
| Situs tampil normal & gambar muncul | Situs **baik-baik saja**; masalah sebelumnya hanya cache | Bersihkan cache (Bagian 8.8) |
| Situs tetap bermasalah | Masalahnya **di repositori**, bukan cache | Telusuri Bagian 8.1–8.7 |
| Halaman 404 di incognito | Penerbitan belum selesai / pengaturan Pages salah | Cek **Settings → Pages** dan tab **Actions** |

> **Tips:** incognito juga berguna untuk memastikan tidak ada ekstensi browser Anda yang
> mengganggu (misalnya pemblokir iklan yang memblokir gambar atau script).

### 8.10 Tabel ringkas masalah & solusi

| Gejala | Kemungkinan penyebab | Solusi cepat |
|---|---|---|
| Halaman 404 | Penerbitan belum selesai / Pages belum diaktifkan / branch & folder salah | Tunggu 1–2 menit; cek **Settings → Pages** (Bagian 8.1) |
| Gambar tidak muncul | Folder `images/` tidak terunggah, atau `index.html` di subfolder | Unggah folder `images`; pastikan struktur sejajar (Bagian 8.2) |
| CSS/JS tidak jalan | JavaScript nonaktif, berkas tidak lengkap, cache | Aktifkan JS; unggah ulang; hard refresh (Bagian 8.3) |
| Situs tampil sebagai kode mentah | Berkas tidak bernama `index.html` / ada di subfolder / folder root salah | Ganti nama ke `index.html`; pindah ke akar; folder `/ (root)` (Bagian 8.4) |
| `.nojekyll` hilang | Aplikasi ekstrak mengabaikan berkas bertitik | Buat ulang (Bagian 8.5) |
| Situs tidak dapat diterbitkan | Repositori **Private** | Ubah ke **Public** (Bagian 8.6) |
| Halaman 404 padahal berkas ada | Folder **/docs** dipilih | Ubah ke **/ (root)** (Bagian 8.7) |
| Perubahan tidak muncul | Cache browser / penerbitan belum selesai | Hard refresh, bersihkan cache, cek tab Actions (Bagian 8.8) |
| Masih bingung masalahnya di mana | Tidak bisa dibedakan cache vs repositori | Buka di mode incognito (Bagian 8.9) |
| `robots.txt` / `sitemap.xml` tampil 404 | Kedua berkas belum terunggah, atau berada di subfolder | Unggah ke level paling atas (Bagian 8.11) |
| `sitemap.xml` tampil dengan pesan kesalahan XML | Tanda `<` `>` atau garis miring rusak saat mengedit | Perbaiki formatnya (Bagian 8.11) |
| Tombol Beli tidak berfungsi | Blokir pop-up aktif di browser | Izinkan pop-up untuk situs Anda, lalu klik ulang |
| Tombol Bagikan tidak tampil | `index.html` versi lama masih di cache repositori | Unggah ulang `index.html` terbaru, lalu hard refresh (Bagian 8.12) |
| Panel Bagikan tidak terbuka | JavaScript diblokir / berkas rusak saat disunting | Aktifkan JS; muat ulang berkas dari ZIP (Bagian 8.12) |

### 8.11 `robots.txt` atau `sitemap.xml` bermasalah

**Gejala A — membuka alamat berkas menampilkan halaman 404**

Berarti berkasnya belum ada di repositori, atau berada di tempat yang salah.

1. Buka halaman utama repositori Anda di GitHub.
2. Pastikan `robots.txt` dan `sitemap.xml` **terlihat di daftar berkas tingkat atas**,
   sejajar dengan `index.html`.
3. Bila tidak ada: kembali ke [Bagian 3](#bagian-3--upload-berkas-ke-repositori) dan
   unggah keduanya.
4. Bila berada di dalam subfolder: pindahkan ke akar. Cara termudah — buka berkasnya →
   klik ikon **pensil** → ubah **nama berkas** menjadi `robots.txt` (tanpa awalan folder) →
   **Commit changes**; lalu hapus berkas lama di subfolder.
5. Tunggu 1–2 menit dan buka ulang alamatnya.

**Gejala B — `sitemap.xml` terbuka tetapi menampilkan pesan kesalahan XML**

Browser menampilkan kalimat seperti *"This page contains the following errors"* beserta
keterangan posisi baris. Penyebabnya hampir selalu ada karakter yang rusak saat mengedit.

Periksa hal-hal berikut:

| Yang diperiksa | Benar | Salah |
|---|---|---|
| Baris pembuka | `<?xml version="1.0" encoding="UTF-8"?>` | baris ini terhapus / berubah |
| Tag pembuka & penutup | `<urlset …>` … `</urlset>` | salah satunya hilang |
| Blok URL | `<url>` … `</url>` berpasangan | hanya ada `<url>` tanpa penutup |
| Alamat situs | `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/` | huruf besar/kecil tidak sama, atau masih ada sisa tanda `<` `>` |
| Tanda ampersand | ditulis `&amp;` bila perlu | ada `&` berdiri sendiri |

**Cara memperbaiki:** buka berkasnya di GitHub → klik pensil (*Edit this file*) → bandingkan
dengan tabel di atas → **Commit changes** → tunggu 1–2 menit → muat ulang di browser.

> **Cara paling aman:** salin ulang isi asli `sitemap.xml` dari dalam ZIP paket (berkas ini
tidak pernah berubah), karena alamat di dalamnya sudah benar.

**Gejala C — berkas tampil normal, tetapi mesin pencari belum mengindeks**

Wajar. Pengindeksan butuh waktu (hari sampai minggu) dan tidak bisa dipaksa. Yang penting
kedua berkas sudah dapat dibuka di browser dan alamatnya sudah cocok satu sama lain.

---

### 8.12 Tombol Bagikan bermasalah

**Gejala A — tombol Bagikan tidak muncul di kartu produk**

Berarti `index.html` di repositori masih versi lama (sebelum fitur Bagikan ditambahkan),
atau browser Anda masih menampilkan versi dari cache.

1. Buka halaman repositori di GitHub → klik **`index.html`**.
2. Tekan **Ctrl + F** / **Cmd + F**, cari teks `btn-share`.
   - **Bila ditemukan:** berkas di repositori sudah benar → masalahnya **cache browser**.
     Lakukan **hard refresh** (**Ctrl + Shift + R** / **Cmd + Shift + R**) atau buka di
     **mode incognito** — lihat [Bagian 8.9](#89-cara-memeriksa-lewat-mode-incognito).
   - **Bila tidak ditemukan:** berkas di repositori masih lama → unggah ulang `index.html`
     dari ZIP paket terbaru (lihat [Bagian 7.1](#71-mengubah-teks--struktur-halaman)),
     lalu tunggu 1–2 menit.

**Gejala B — tombol tampak, tetapi panel tidak terbuka saat diklik**

1. Pastikan **JavaScript aktif** di browser (lihat [Bagian 8.3](#83-css--javascript-tidak-jalan-halaman-tampil-polos-tanpa-gaya)).
2. Muat ulang halaman dengan **hard refresh** — panel digerakkan oleh JavaScript, jadi bila
   berkasnya terpotong saat disunting, tombol akan tampak tetapi tidak bereaksi.
3. Bila Anda pernah menyunting `index.html` secara manual, kembalikan berkas itu dari ZIP
   paket (pilih **Add file ▾ → Upload files** dan unggah `index.html` yang baru).

**Gejala C — panel terbuka, tetapi media sosial tidak mau terbuka**

| Kemungkinan | Cara memastikan | Solusi |
|---|---|---|
| Pemblokir pop-up | Muncul ikon/peringatan pemblokir di address bar | Izinkan pop-up untuk situs Anda, lalu klik ulang |
| Pemblokir iklan/privasi agresif | Panel terbuka, tetapi tidak ada tab baru | Nonaktifkan pemblokir untuk situs Anda, lalu uji ulang |
| Sedang dalam mode incognito dengan blokir ketat | Hanya di mode incognito | Uji di mode normal |

> **Catatan:** pada minggu-minggu awal setelah situs terbit, jendela berbagi Facebook atau X
> kadang menampilkan peringatan bahwa tautannya belum terbaca. Ini normal dan akan hilang
> dengan sendirinya setelah halaman dikenali — tidak perlu tindakan apa pun.

**Gejala D — tombol "Salin tautan" menampilkan notifikasi gagal**

1. Pastikan halaman dibuka lewat **alamat `https://…`** (GitHub Pages selalu `https`), bukan
   dibuka langsung dari berkas di komputer. Penyalinan otomatis memerlukan koneksi aman.
2. Klik sekali lagi di area halaman, lalu coba tombol **Salin tautan** kembali.
3. Bila tetap gagal, salin manual: klik kanan pada kartu produk → *Copy link address*, atau
   tempel alamat situs yang tertulis di [Bagian 6](#bagian-6--tunggu--verifikasi-situs-live).

---

## Bagian 9 — FAQ & Daftar Periksa

### 9.1 FAQ singkat

**T: Apakah saya perlu bisa programming?**
J: Tidak. Seluruh proses hanya klik-klik di browser. Tidak perlu menulis kode, tidak perlu
terminal, tidak perlu Git.

**T: Apakah GitHub Pages benar-benar gratis?**
J: Ya, gratis untuk repositori **Public**. Tidak ada biaya langganan, tidak perlu kartu kredit.

**T: Berapa lama situs akan aktif?**
J: Penerbitan pertama 1–2 menit (kadang sampai 5 menit pada jam sibuk). Pemutakhiran
berikutnya juga 1–2 menit setelah setiap commit.

**T: Apakah situs akan tetap online selamanya?**
J: Selama repositori tetap ada dan berstatus Public, situs akan terus aktif. Tidak ada
batas waktu.

**T: Di mana saya mengubah harga produk?**
J: Di dalam `index.html`, pada blok `PRODUCTS` — cari `price: 50000`. Ubah angkanya
(tanpa titik), lalu commit. Situs diperbarui otomatis dalam 1–2 menit.

**T: Bagaimana bila saya ingin mengganti tombol Beli agar mengarah ke link checkout lain?**
J: Ubah satu baris di `index.html`:

```js
var CHECKOUT_BELANDA_IRIAN_JAYA = 'https://tokopapuaonline.orderhero.id/form/checkout-belanda-irian-jaya';
var CHECKOUT_URL = 'https://tokopapuaonline.orderhero.id/store';
```

Setiap produk juga punya kolom `url` sendiri di dalam blok `PRODUCTS`. Bila sebuah produk
belum diisi `url`, tombol Beli memakai tautan cadangan `CHECKOUT_URL`.

**Catatan penting:** saat ini **kedua produk memakai `CHECKOUT_BELANDA_IRIAN_JAYA`**,
karena produk **"Laporan Tindak Kekerasan di Papua - Gugus Tugas UGM"** belum memiliki
halaman checkout sendiri (sudah diuji 2026-09-21 — beberapa varian slug mengarah ke
halaman Not Found). Ubah `url` pada objek `laporan-kekerasan-papua` begitu tautan
checkout khususnya tersedia.

**T: Ada tombol Bagikan di kartu produk — apa fungsinya?**
J: Tombol itu untuk membagikan produk ke media sosial: **WhatsApp, Facebook, X/Twitter,
Telegram**, atau **Salin tautan**. Yang terkirim adalah **nama produk + alamat situs**,
jadi penerima langsung tahu produk apa yang sedang dibagikan. Tombol ini otomatis muncul
di **setiap** kartu produk — lihat penjelasan fiturnya pada **Bagian 8** di `README.md`,
dan cara memeriksanya di [Bagian 6.7](#67-memverifikasi-tombol-bagikan-share).

**T: Apakah tombol Bagikan perlu diatur atau disambungkan ke akun media sosial saya?**
J: Tidak. Tidak ada akun, kunci API, atau pengaturan tambahan. Tautan dibagikan lewat
jendela berbagi resmi masing-masing layanan, dan pengirim tetap memakai akun media sosial
masing-masing saat mengirim.

**T: Bisakah saya mengubah alamat yang dibagikan atau menambah media sosial lain?**
J: Bisa. Alamat yang dibagikan diatur di baris `var PAGE_URL = '...'` di dalam
`index.html`. Langkah lengkapnya ada di
[Bagian 7.6](#76-mengubah-teks--tautan-pada-tombol-bagikan).

**T: Apakah halaman ini bisa dibuka di HP?**
J: Ya. Halaman sudah responsif penuh — diuji pada **390 × 844** (HP) dan **1280 × 900**
(PC), tanpa scroll horizontal pada keduanya.

**T: Apakah perlu internet khusus atau server tambahan?**
J: Tidak. Paket ini berisi HTML/CSS/JavaScript dan gambar statis, tanpa dependensi
eksternal, tanpa proses build, dan tanpa panggilan ke layanan pihak ketiga.

**T: Ada dua berkas tambahan, `robots.txt` dan `sitemap.xml`. Apakah wajib diunggah?**
J: Tidak wajib untuk tampilan halaman — keduanya tidak memengaruhi cara halaman dirender.
Namun keduanya sudah termasuk dalam paket, jadi cukup seret ikut saat mengunggah. Fungsinya
membantu mesin pencari mengenali situs Anda. Detail: [Bagian 6.6](#66-memverifikasi-robotstxt--sitemapxml).

**T: Apakah saya harus mengganti isi `robots.txt` dan `sitemap.xml`?**
J: Tidak. Keduanya **sudah terisi** dengan URL GitHub Pages paket ini
(`https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/`), jadi cukup diunggah apa
adanya — tidak ada placeholder yang perlu diganti.

**T: Saya ingin memakai nama repositori lain. Apakah alamat di kedua berkas masih benar?**
J: Tidak lagi. Bila nama repo berbeda, alamat situs Anda juga berbeda, jadi perbarui dulu
alamat di `robots.txt` dan `sitemap.xml` agar cocok dengan nama repo Anda — cara:
[Bagian 7.5](#75-memperbarui-robotstxt--sitemapxml).

**T: Apakah `robots.txt` bisa membuat situs saya tersembunyi dari Google?**
J: Tidak. Berkas ini justru berbunyi `User-agent: *` dan `Allow: /`, artinya **semua crawler
diizinkan** mengindeks seluruh isi situs.

**T: Bisakah saya memakai nama repositori lain?**
J: Bisa. Nama repo hanya mempengaruhi bagian akhir URL situs Anda. Ikuti aturan penamaan
di [Bagian 2.2](#22-membuat-repositori-baru).

**T: Berapa ukuran total paket?**
J: Sekitar 440 KB setelah diekstrak — sangat ringan dan cepat dibuka.

**T: Apakah `README.md` dan `panduan-upload-github.md` akan tampil di situs?**
J: Tidak. Keduanya hanya berkas dokumentasi di repositori dan tidak dipanggil oleh
`index.html`, sehingga tidak terlihat pengunjung situs.

**T: Apakah perlu berkas konfigurasi tambahan?**
J: Tidak. Situs diterbitkan langsung pada alamat bawaan GitHub Pages (`github.io`), jadi
seluruh berkas konfigurasi tambahan tidak diperlukan — paket ini sudah lengkap apa adanya.

**T: Bolehkah saya memperbarui isi situs nanti?**
J: Ya, kapan saja — lihat [Bagian 7](#bagian-7--memperbarui-situs-di-kemudian-hari).

### 9.2 Daftar periksa (checklist) — centang satu per satu

**Sebelum mengunggah**

- [ ] Berkas ZIP `toko-papua-online-store-paket-github.zip` sudah diunduh.
- [ ] ZIP sudah **diekstrak** ke sebuah folder.
- [ ] Sudah memastikan `index.html` berada di **level paling atas** folder hasil ekstrak.
- [ ] Sudah memastikan folder `images/` berada **sejajar** dengan `index.html`.
- [ ] Sudah memastikan folder `images/` berisi **5 gambar**: `logo.webp`, `banner-1.webp`,
      `banner-2.webp`, `produk-1.webp`, `produk-2.webp`.
- [ ] Sudah menampilkan berkas tersembunyi & memastikan `.nojekyll` ada
      *(opsional — bila hilang, lihat Bagian 1.6)*.
- [ ] Sudah punya akun GitHub dan berhasil **masuk (sign in)**.

**Membuat repositori**

- [ ] Repositori baru sudah dibuat dengan nama `toko-papua-online`
      *(atau nama lain sesuai pilihan Anda)*.
- [ ] **Visibility = Public**.
- [ ] **Tidak** mencentang *Add a README file*.
- [ ] **Tidak** menambahkan *.gitignore* maupun *license*.

**Mengunggah berkas**

- [ ] Seluruh **isi** folder sudah diseret ke **Add file ▾ → Upload files**
      *(bukan folder pembungkusnya)*.
- [ ] Folder `images/` ikut terunggah (kelima gambar terlihat di daftar).
- [ ] Pesan commit sudah diisi, lalu **Commit changes** diklik.

**Memeriksa upload**

- [ ] `index.html` terlihat di **halaman utama** repositori.
- [ ] Folder `images` terlihat sejajar dengan `index.html`.
- [ ] `README.md` dan `panduan-upload-github.md` terlihat.
- [ ] `robots.txt` dan `sitemap.xml` terlihat.
- [ ] `.nojekyll` terlihat *(opsional)*.
- [ ] Branch yang aktif adalah **main**.

**Mengaktifkan GitHub Pages**

- [ ] **Settings → Pages** sudah dibuka.
- [ ] **Source = Deploy from a branch**.
- [ ] **Branch = main**, **Folder = / (root)**.
- [ ] Tombol **Save** sudah diklik.

**Memverifikasi situs live**

- [ ] Sudah menunggu **1–2 menit**.
- [ ] URL `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/` sudah dibuka.
- [ ] Halaman toko tampil (bukan 404).
- [ ] Logo, kedua banner, dan kedua sampul produk **tampil semua**.
- [ ] Grid produk tampil dengan harga `Rp 50.000`.
- [ ] Tombol **🛒 Beli** terlihat di setiap kartu produk.
- [ ] **Klik tombol Beli produk 1** → tab baru terbuka ke
      `https://tokopapuaonline.orderhero.id/form/checkout-belanda-irian-jaya`.
- [ ] **Klik tombol Beli produk 2** → tab baru terbuka ke
      `https://tokopapuaonline.orderhero.id/form/checkout-belanda-irian-jaya`
      *(belum ada tautan checkout khusus untuk produk ini).*
- [ ] Tampilan **mobile (390 × 844)** rapi: 2 kolom produk, bottom tab bar muncul,
      tanpa scroll horizontal.
- [ ] Tampilan **desktop (1280 × 900)** rapi: menu navigasi & tombol keranjang muncul,
      grid 3–4 kolom, tanpa scroll horizontal.
- [ ] Footer tampil dan tidak ada elemen bertumpuk atau terpotong.
- [ ] `robots.txt` terbuka di browser dan memuat baris `Sitemap:`.
- [ ] `sitemap.xml` terbuka di browser tanpa pesan kesalahan XML.
- [ ] `robots.txt` dan `sitemap.xml` **sudah terisi** dengan alamat
      `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/` (tanpa placeholder).
- [ ] Tombol **Bagikan** (ikon bagikan) terlihat di **setiap** kartu produk.
- [ ] **Klik tombol Bagikan** → panel muncul dengan 5 pilihan: WhatsApp, Facebook,
      X/Twitter, Telegram, dan **Salin tautan**.
- [ ] **Klik Salin tautan** → muncul notifikasi *"Tautan produk disalin"*.
- [ ] Panel Bagikan dapat ditutup lewat **klik di luar area**, tombol **×**, dan tombol **Esc**.
- [ ] Setelah panel Bagikan ditutup, tombol **🛒 Beli** tetap berfungsi seperti biasa.

---

## Catatan Penutup

- Paket ini berisi halaman web beserta asetnya saja. Situs diterbitkan langsung pada
  alamat bawaan GitHub Pages (`github.io`) — tidak ada langkah konfigurasi tambahan
  di luar panduan ini.
- Seluruh berkas yang dibutuhkan sudah lengkap di dalam folder hasil ekstrak. **Tidak ada
  dependensi eksternal, CDN, maupun proses build yang perlu dijalankan.**
- Bila di kemudian hari Anda memindahkan situs ke alamat lain, hal itu dapat dilakukan
  dari **Settings → Pages** pada repositori Anda.

**Butuh bantuan lebih lanjut?** Buka repositori Anda, klik tab **Actions** untuk melihat
log penerbitan, atau kembali ke panduan ini dan telusuri
[Bagian 8](#bagian-8--pemecahan-masalah-troubleshooting).
