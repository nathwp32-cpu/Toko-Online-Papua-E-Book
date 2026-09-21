# Panduan Upload ke GitHub Pages — Toko Papua Online

Panduan ini menjelaskan **langkah demi langkah, sangat rinci**, cara menerbitkan halaman
toko **Toko Papua Online** dari paket ZIP ini ke GitHub Pages hingga situsnya aktif dan
dapat dibuka publik.

Hasil akhir: halaman toko aktif pada alamat
`https://<username-github-anda>.github.io/<nama-repo>/`

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

> **Inti yang paling sering salah:** pastikan berkas `index.html` berada **di tingkat paling
> atas** repositori (sejajar dengan folder `images/`), **bukan** di dalam subfolder. Ini
> penyebab nomor satu situs menampilkan halaman 404 atau tampil tanpa gambar.

---

## Bagian 1 — Persiapan: Ekstrak Paket ZIP

### 1.1 Isi paket

Paket ZIP bernama **`toko-papua-online-store-paket-github.zip`** berisi **9 berkas**:

| # | Berkas | Keterangan | Ukuran |
|---|---|---|---|
| 1 | `index.html` | Halaman toko utama (mobile + desktop, satu berkas) | ± 50 KB |
| 2 | `README.md` | Ringkasan proyek | ± 6,5 KB |
| 3 | `panduan-upload-github.md` | Berkas panduan ini | ± 6,6 KB |
| 4 | `.nojekyll` | Berkas kosong (0 byte) penanda untuk GitHub Pages | 0 byte |
| 5 | `images/logo.webp` | Logo toko (header & footer) | ± 112 KB |
| 6 | `images/banner-1.webp` | Banner promo carousel 1 | ± 44 KB |
| 7 | `images/banner-2.webp` | Banner promo carousel 2 | ± 97 KB |
| 8 | `images/produk-1.webp` | Sampul produk 1 | ± 95 KB |
| 9 | `images/produk-2.webp` | Sampul produk 2 | ± 34 KB |

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
     (`https://<username>.github.io/...`). Gunakan huruf kecil, angka, dan tanda hubung.
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

**Rekomendasi nama repositori:**

| Nama repo | Alamat situs hasil | Catatan |
|---|---|---|
| `toko-papua-online` | `https://<username>.github.io/toko-papua-online/` | **Disarankan** — jelas & mudah diingat |
| `store` | `https://<username>.github.io/store/` | Singkat |
| `<username>.github.io` | `https://<username>.github.io/` | Situs di akar; hanya boleh **satu** repo dengan nama ini |

> **Aturan penamaan:** gunakan huruf kecil, angka, dan tanda hubung (`-`). Hindari spasi,
> huruf besar, dan karakter khusus. Nama repo akan menjadi bagian dari alamat situs Anda.

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
   `.nojekyll` (bila terlihat), dan folder **`images`**.

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

Klik folder **`images`** untuk memastikan kelima gambar ada di dalamnya:
`logo.webp`, `banner-1.webp`, `banner-2.webp`, `produk-1.webp`, `produk-2.webp`.

### 4.2 Daftar periksa cepat

- [ ] `index.html` terlihat **di halaman utama repositori** (bukan di dalam subfolder).
- [ ] Folder `images` terlihat **sejajar** dengan `index.html`.
- [ ] Di dalam `images/` terdapat **5 gambar** dengan nama yang benar.
- [ ] `README.md` dan `panduan-upload-github.md` ikut terunggah.
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

   > **Your site is live at `https://<username>.github.io/<nama-repo>/`**

   Alamat di kotak itulah **URL situs Anda**. Klik **Visit site** untuk membukanya,
   atau salin alamatnya.

> **Bila tombol Save tidak muncul atau opsi Pages tidak ada:** pastikan repositori
> berstatus **Public** (lihat [Bagian 2.2](#22-membuat-repositori-baru) dan
> [Bagian 8.6](#86-repositori-private--situs-tidak-dapat-diterbitkan)).

### 5.1 Cara menemukan URL situs Anda

URL situs selalu berpola:

```
https://<username-github-anda>.github.io/<nama-repo>/
```

**Contoh:** bila username GitHub Anda `namasaya` dan nama repo `toko-papua-online`:

```
https://namasaya.github.io/toko-papua-online/
```

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
4. Tunggu 1–2 menit. Kartu produk baru akan muncul otomatis — filter, pencarian, dan
   keranjang menyesuaikan sendiri tanpa perubahan kode lain.

### 7.4 Memastikan perubahan sudah terbit

1. Buka tab **Actions** di repositori.
2. Cari alur terbaru bernama **pages build and deployment**.
3. Pastikan statusnya **✅ hijau** dan selesai (bukan berputar / ⏳).
4. Buka situs Anda dengan **mode incognito** atau **hard refresh** untuk memastikan
   Anda tidak melihat versi lama dari cache browser.
5. Bila perubahan masih belum tampak setelah 5 menit, lihat
   [Bagian 8.8](#88-cache-browser-menampilkan-versi-lama).

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
7. **Alamat salah tulis** — pastikan formatnya
   `https://<username>.github.io/<nama-repo>/` dan ada garis miring `/` di akhir.
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
`https://<username>.github.io/<nama-repo>/images/logo.webp`.
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
   `https://<username>.github.io/<nama-repo>/` (tanpa nama berkas di akhir).

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
   `https://<username>.github.io/<nama-repo>/?v=2`.

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
| Tombol Beli tidak berfungsi | Blokir pop-up aktif di browser | Izinkan pop-up untuk situs Anda, lalu klik ulang |

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

**T: Apakah halaman ini bisa dibuka di HP?**
J: Ya. Halaman sudah responsif penuh — diuji pada **390 × 844** (HP) dan **1280 × 900**
(PC), tanpa scroll horizontal pada keduanya.

**T: Apakah perlu internet khusus atau server tambahan?**
J: Tidak. Paket ini berisi HTML/CSS/JavaScript dan gambar statis, tanpa dependensi
eksternal, tanpa proses build, dan tanpa panggilan ke layanan pihak ketiga.

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
- [ ] `.nojekyll` terlihat *(opsional)*.
- [ ] Branch yang aktif adalah **main**.

**Mengaktifkan GitHub Pages**

- [ ] **Settings → Pages** sudah dibuka.
- [ ] **Source = Deploy from a branch**.
- [ ] **Branch = main**, **Folder = / (root)**.
- [ ] Tombol **Save** sudah diklik.

**Memverifikasi situs live**

- [ ] Sudah menunggu **1–2 menit**.
- [ ] URL `https://<username>.github.io/<nama-repo>/` sudah dibuka.
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
