# Panduan Upload ke GitHub Pages

Panduan ini menjelaskan cara menerbitkan halaman toko **Toko Papua Online** dari paket
ZIP ini ke GitHub Pages, langkah demi langkah, memakai alamat bawaan GitHub Pages.

Hasil akhir: halaman toko dapat diakses publik melalui alamat
`https://<username>.github.io/<nama-repo>/`.

**Perkiraan waktu: 3–5 menit.**

---

## Ringkasan Alur

1. Unduh dan ekstrak paket ZIP.
2. Buat akun/masuk ke GitHub.
3. Buat repositori baru berstatus **Public**.
4. Unggah berkas paket ke repositori.
5. Aktifkan GitHub Pages.
6. Tunggu 1–2 menit, lalu buka alamat situs.

---

## Langkah 1 — Unduh dan Ekstrak Paket

1. Unduh berkas **`toko-papua-online-store-paket-github.zip`**.
2. Ekstrak (unzip) berkas tersebut ke sebuah folder di komputer.

Setelah diekstrak, isi folder harus terlihat seperti ini:

```
toko-papua-online-store-paket-github/
├── index.html
├── README.md
├── panduan-upload-github.md
├── .nojekyll
└── images/
    ├── logo.webp
    ├── banner-1.webp
    ├── banner-2.webp
    ├── produk-1.webp
    └── produk-2.webp
```

> **Penting:** `index.html` harus berada di tingkat paling atas folder, bukan di dalam
> subfolder. Folder `images/` harus berada tepat di samping `index.html`, karena
> halaman merujuk gambar dengan jalur relatif (`images/logo.webp`).

> **Catatan berkas `.nojekyll`:** berkas ini tidak memiliki isi (0 byte) dan di beberapa
> sistem tersembunyi karena diawali titik. Berkas ini mencegah GitHub Pages memproses
> situs dengan Jekyll. Berkas ini opsional — bila tidak ikut terunggah, situs tetap
> berfungsi.

---

## Langkah 2 — Masuk ke GitHub

1. Buka **https://github.com**.
2. Bila belum punya akun, klik **Sign up** dan ikuti proses pendaftaran.
3. Bila sudah punya, klik **Sign in** dan masuk.

---

## Langkah 3 — Buat Repositori Baru

1. Setelah masuk, klik ikon **+** di pojok kanan atas, lalu pilih **New repository**.
   Atau langsung buka **https://github.com/new**.
2. Isi kolom berikut:
   - **Repository name**: misalnya `toko-papua-online`
     (gunakan huruf kecil dan tanda hubung; hindari spasi)
   - **Description**: opsional, misalnya `Halaman toko Toko Papua Online`
   - **Visibility**: pilih **Public**
     > GitHub Pages gratis hanya tersedia untuk repositori **Public**. Bila memilih
     > Private, situs tidak dapat diterbitkan tanpa paket berbayar.
3. **Jangan** centang *Add a README file*, *Add .gitignore*, atau *Choose a license* —
   biarkan kosong agar tidak terjadi konflik berkas saat mengunggah nanti.
4. Klik **Create repository**.

---

## Langkah 4 — Unggah Berkas ke Repositori

Setelah repositori dibuat, Anda akan melihat halaman dengan pesan
*"Quick setup — if you've done this kind of thing before"*.

1. Klik tautan **uploading an existing file** di bagian tengah halaman.
   (Atau klik tombol **Add file ▾** di kanan atas, lalu pilih **Upload files**.)
2. Buka folder hasil ekstrak di komputer Anda.
3. Pilih **semua berkas dan folder** di dalamnya, lalu seret (drag and drop)
   ke area unggah di halaman GitHub.
   - Pastikan `index.html` ikut terpilih.
   - Pastikan folder `images/` ikut terpilih beserta seluruh isinya.
   - Bila berkas `.nojekyll` tidak ikut terpilih (tersembunyi), tidak masalah —
     lanjutkan saja.
4. Tunggu hingga seluruh berkas selesai diunggah. Jumlah berkas yang terunggah akan
   terlihat pada daftar di bawah kotak unggah.
5. Pada kolom **Commit changes**, biarkan pesan bawaan atau tulis misalnya
   `Tambah halaman toko`.
6. Klik tombol **Commit changes**.

Setelah selesai, halaman repositori akan menampilkan berkas `index.html`, `README.md`,
`panduan-upload-github.md`, dan folder `images`.

---

## Langkah 5 — Aktifkan GitHub Pages

1. Di halaman repositori, klik tab **Settings** (ikon roda gigi di deretan menu atas).
2. Pada panel kiri, gulir ke bawah dan klik **Pages**
   (di bawah bagian *Code and automation*).
3. Pada bagian **Build and deployment**:
   - **Source**: pilih **Deploy from a branch**
   - **Branch**: pilih **main**, lalu pilih folder **/ (root)**
   - Klik **Save**
4. Tunggu sebentar. Muat ulang halaman **Settings → Pages**.
   Sebuah kotak akan muncul berisi pesan *"Your site is live at ..."*
   beserta alamat situs Anda.

---

## Langkah 6 — Buka Situs

Alamat situs berbentuk:

```
https://<username-github-anda>.github.io/<nama-repo>/
```

Contoh: bila username Anda `namasaya` dan nama repo `toko-papua-online`, maka alamatnya:

```
https://namasaya.github.io/toko-papua-online/
```

Buka alamat tersebut. Halaman toko akan langsung tampil.

> Penerbitan pertama biasanya memerlukan **1–2 menit**. Bila muncul halaman 404,
> tunggu sekitar satu menit lalu muat ulang. Bila masih 404 setelah 5 menit, periksa
> kembali Langkah 5 (pastikan branch `main` dan folder `/ (root)` sudah benar).

---

## Memperbarui Situs di Kemudian Hari

Setiap kali Anda ingin mengubah isi situs:

1. Buka repositori Anda di GitHub.
2. Klik berkas yang ingin diubah (misalnya `index.html`).
3. Klik ikon pensil (**Edit this file**), lakukan perubahan, lalu **Commit changes**.
4. Untuk mengganti gambar: buka folder `images/`, klik **Add file ▾ → Upload files**,
   unggah gambar baru dengan nama berkas yang sama.
5. Tunggu 1–2 menit, lalu muat ulang situs.

---

## Pemecahan Masalah

| Gejala | Penyebab & solusi |
|---|---|
| Halaman 404 setelah diaktifkan | Tunggu 1–2 menit lalu muat ulang. Bila tetap, periksa **Settings → Pages**: branch harus `main` dan folder `/ (root)`. |
| Situs tampil tanpa gambar | Folder `images/` tidak ikut terunggah, atau `index.html` berada di dalam subfolder. Pastikan `index.html` sejajar dengan folder `images/`. |
| Situs menampilkan kode/README | Berkas utama harus bernama tepat `index.html` (huruf kecil semua). Ganti nama bila perlu. |
| Perubahan tidak muncul | Tunggu 1–2 menit. Bila tetap, lakukan *hard refresh* (Ctrl/Cmd + Shift + R) untuk membersihkan tembolok peramban. |
| Tombol **Save** di halaman Pages tidak muncul | Pastikan repositori berstatus **Public**. |
| Situs tampil tanpa gaya/tata letak | JavaScript dinonaktifkan di peramban. Aktifkan JavaScript, lalu muat ulang. |

---

## Catatan

- Paket ini berisi halaman web dan asetnya saja. Situs diterbitkan langsung pada
  alamat bawaan GitHub Pages (`github.io`), jadi tidak ada pengaturan tambahan yang
  perlu Anda siapkan selain langkah-langkah di atas.
- Seluruh berkas yang dibutuhkan sudah lengkap di dalam folder hasil ekstrak. Tidak ada
  dependensi eksternal, CDN, maupun proses build yang perlu dijalankan.
