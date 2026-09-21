# Panduan Setup Domain Kustom — tokopapuaonline.com

Panduan lengkap dalam Bahasa Indonesia untuk menghubungkan landing page **Toko Papua Online** ke domain sendiri: **`tokopapuaonline.com`** melalui GitHub Pages.

Tidak perlu bisa programming. Ikuti saja urutannya dari atas ke bawah.

> **Sudah siap di paket ini:** file `CNAME` sudah dibuat dan sudah berisi `tokopapuaonline.com`. File `sitemap.xml`, `robots.txt`, dan tag `<link rel="canonical">` + `og:url` di `index.html` juga sudah menunjuk ke domain ini. Yang perlu Anda lakukan tinggal **mengatur DNS di registrar** dan **mengaktifkan Custom domain di GitHub**.

---

## 📋 Daftar Isi

1. [Sebelum Mulai](#1-sebelum-mulai)
2. [Tabel Record DNS yang Harus Dibuat](#2-tabel-record-dns-yang-harus-dibuat)
3. [Cara Menambahkan Record DNS di Registrar / Cloudflare](#3-cara-menambahkan-record-dns-di-registrar--cloudflare)
4. [Mengaktifkan Custom Domain di GitHub Pages](#4-mengaktifkan-custom-domain-di-github-pages)
5. [Verifikasi DNS (nslookup / dig) & Waktu Propagasi](#5-verifikasi-dns-nslookup--dig--waktu-propagasi)
6. [Mengaktifkan HTTPS (Enforce HTTPS)](#6-mengaktifkan-https-enforce-https)
7. [Troubleshooting](#7-troubleshooting)
8. [Cara Menghapus / Mengganti Domain](#8-cara-menghapus--mengganti-domain)
9. [⚠️ Catatan Penting: File CNAME Jangan Dihapus](#9-️-catatan-penting-file-cname-jangan-dihapus)
10. [Checklist Akhir](#10-checklist-akhir)

---

## 1. Sebelum Mulai

### Yang harus sudah beres lebih dulu

| Syarat | Keterangan |
|--------|------------|
| **Situs sudah jalan di GitHub Pages** | Buka `https://<username>.github.io/<nama-repo>/` — harus tampil landing page-nya, bukan 404 |
| **Sudah punya domain** | `tokopapuaonline.com` sudah dibeli dan bisa Anda kelola di registrar (Cloudflare, Niagahoster, Namecheap, Rumahweb, GoDaddy, dsb.) |
| **Akses ke pengaturan DNS** | Punya login ke dashboard registrar tempat domain itu dibeli |
| **Akses ke repository GitHub** | Login sebagai pemilik repository landing page |

### Tiga hal yang akan terjadi

1. Anda menambahkan **record DNS** di registrar → memberi tahu internet bahwa domain ini "menunjuk ke GitHub".
2. Anda mengisi **Custom domain** di GitHub → GitHub mulai melayani domain tersebut.
3. GitHub menerbitkan **sertifikat HTTPS** otomatis (gratis, dari Let's Encrypt) → sekitar 15 menit sampai 24 jam.

> **Urutan yang disarankan:** kerjakan **Bagian 2 & 3 (DNS) lebih dulu**, baru **Bagian 4 (GitHub)**. Kalau dibalik pun tidak masalah — GitHub akan terus mencoba memverifikasi sendiri setelah DNS benar.

### Kenali istilahnya

| Istilah | Arti singkat |
|---------|--------------|
| **A record** | Memetakan sebuah nama domain ke **alamat IP** (deretan angka seperti `185.199.108.153`) |
| **CNAME record** | Memetakan sebuah nama domain ke **nama domain lain** (misal `www` → `username.github.io`) |
| **`@`** | Simbol untuk **domain utama** itu sendiri (di sini: `tokopapuaonline.com` tanpa `www`) |
| **TTL** | *Time To Live* — berapa lama record DNS di-*cache*. Pakai **Auto** atau **3600** saja |
| **Propagasi** | Proses menyebarnya perubahan DNS ke seluruh dunia. Butuh 5 menit – 24 jam |

---

## 2. Tabel Record DNS yang Harus Dibuat

Buat record berikut di dashboard DNS domain **`tokopapuaonline.com`**.

> **Ganti `<username>`** dengan username GitHub Anda. Contoh: kalau username GitHub Anda `tokopapua`, maka targetnya `tokopapua.github.io`.

### 2.1 Domain utama — 4 A record

| Type | Name / Host | Value / Points to | TTL | Keterangan |
|------|-------------|-------------------|-----|------------|
| **A** | `@` | `185.199.108.153` | Auto / 3600 | GitHub Pages IP #1 |
| **A** | `@` | `185.199.109.153` | Auto / 3600 | GitHub Pages IP #2 |
| **A** | `@` | `185.199.110.153` | Auto / 3600 | GitHub Pages IP #3 |
| **A** | `@` | `185.199.111.153` | Auto / 3600 | GitHub Pages IP #4 |

Keempat record ini **wajib dibuat semuanya**. Fungsinya untuk *failover* — kalau satu server GitHub bermasalah, yang lain tetap melayani.

### 2.2 Subdomain www — 1 CNAME record

| Type | Name / Host | Value / Points to | TTL | Keterangan |
|------|-------------|-------------------|-----|------------|
| **CNAME** | `www` | `<username>.github.io` | Auto / 3600 | Contoh: `tokopapua.github.io` |

### 2.3 Alternatif (lebih maju): 4 AAAA record untuk IPv6

Opsional. Tambahkan hanya kalau registrar Anda mendukung record AAAA dan Anda ingin situs juga bisa diakses lewat IPv6.

| Type | Name / Host | Value / Points to | TTL |
|------|-------------|-------------------|-----|
| **AAAA** | `@` | `2606:50c0:8000::153` | Auto / 3600 |
| **AAAA** | `@` | `2606:50c0:8001::153` | Auto / 3600 |
| **AAAA** | `@` | `2606:50c0:8002::153` | Auto / 3600 |
| **AAAA** | `@` | `2606:50c0:8003::153` | Auto / 3600 |

### 2.4 Ringkasan total

| Type | Name | Value | Jumlah |
|------|------|-------|--------|
| A | `@` | `185.199.108.153` | 1 |
| A | `@` | `185.199.109.153` | 1 |
| A | `@` | `185.199.110.153` | 1 |
| A | `@` | `185.199.111.153` | 1 |
| CNAME | `www` | `<username>.github.io` | 1 |
| | | **TOTAL WAJIB** | **5 record** |
| AAAA | `@` | (4 alamat IPv6) | 0–4 *(opsional)* |

### ⚠️ Yang harus DIHAPUS lebih dulu

Sebelum menambahkan record di atas, cek dan **hapus** hal-hal berikut kalau ada — kalau tidak, domain bisa menampilkan halaman aneh atau gagal total:

- **A record lama** yang menunjuk ke IP hosting lain (misal IP hosting lama atau IP parkir registrar)
- **CNAME record `@`** — CNAME di domain utama **tidak boleh** ada bersamaan dengan A record (aturan DNS: CNAME tidak boleh sejajar dengan record lain). Kalau ada, hapus CNAME `@`-nya.
- **Record `www` lama** yang menunjuk ke tempat lain
- **Fitur "Parking" / "Domain forwarding" / "URL redirect"** di registrar — matikan dulu

---

## 3. Cara Menambahkan Record DNS di Registrar / Cloudflare

### 3.1 Contoh A — Cloudflare (paling umum)

1. Login ke [dash.cloudflare.com](https://dash.cloudflare.com).
2. Pilih domain **`tokopapuaonline.com`**.
3. Buka menu **DNS** → **Records**.
4. Klik **Add record**, lalu isi:

   | Field | Isi |
   |-------|-----|
   | **Type** | `A` |
   | **Name** | `@` |
   | **IPv4 address** | `185.199.108.153` |
   | **Proxy status** | **DNS only** (ikon awan abu-abu ☁️, bukan oranye) ⚠️ |
   | **TTL** | Auto |

5. Klik **Save**. Ulangi untuk ketiga alamat IP lainnya (`185.199.109.153`, `185.199.110.153`, `185.199.111.153`).
6. **Add record** lagi untuk `www`:

   | Field | Isi |
   |-------|-----|
   | **Type** | `CNAME` |
   | **Name** | `www` |
   | **Target** | `<username>.github.io` |
   | **Proxy status** | **DNS only** (abu-abu) ⚠️ |
   | **TTL** | Auto |

7. Klik **Save**.

> ### 🔴 PENTING untuk pengguna Cloudflare
>
> **Wajib set "Proxy status" ke DNS only (awan abu-abu)** untuk keempat A record dan CNAME `www`.
>
> Kalau dibiarkan **Proxied** (awan oranye), GitHub tidak bisa menerbitkan sertifikat HTTPS-nya sendiri — ini penyebab paling umum dari error *"Domain's DNS record could not be retrieved"* dan sertifikat yang tidak pernah terbit.
>
> Setelah GitHub selesai menerbitkan sertifikat HTTPS-nya (±15 menit–24 jam), Anda **boleh** menyalakan proxy oranye lagi kalau memang mau memakai fitur Cloudflare. Tapi untuk setup pertama: **abu-abu dulu**.

### 3.2 Contoh B — registrar biasa (Niagahoster, Namecheap, GoDaddy, Rumahweb, dsb.)

1. Login ke dashboard registrar tempat Anda membeli domain.
2. Cari menu **DNS Management** / **DNS Zone** / **Kelola DNS** / **Manage DNS Records**.
3. Klik **Add Record** / **Tambah Record** dan isi sesuai tabel di Bagian 2:

   | Field | Untuk A record | Untuk CNAME record |
   |-------|----------------|--------------------|
   | **Type** | `A` | `CNAME` |
   | **Host / Name** | `@` (atau biarkan kosong) | `www` |
   | **Value / Target** | `185.199.108.153` (dst.) | `<username>.github.io` |
   | **TTL** | `3600` (atau Auto) | `3600` (atau Auto) |

4. **Save** satu per satu. Pastikan totalnya **5 record** (4 A + 1 CNAME).

> **Catatan soal tanda titik:** sebagian registrar meminta target diakhiri titik — `tokopapua.github.io.` — sebagian lagi tidak. Kalau muncul error validasi, coba tambahkan titik di akhirnya. Keterangan resminya biasanya ada di tooltip form tersebut.

### 3.3 Setelah menyimpan

Tunggu **5–30 menit** sebelum lanjut ke verifikasi (Bagian 5). DNS butuh waktu menyebar.

---

## 4. Mengaktifkan Custom Domain di GitHub Pages

1. Buka repository landing page Anda di [github.com](https://github.com).
2. Klik tab **Settings** (ikon gerigi, kanan atas).
3. Di menu samping kiri, klik **Pages**.
4. Pastikan bagian **Build and deployment** sudah benar:

   | Pengaturan | Nilai |
   |------------|-------|
   | **Source** | Deploy from a branch |
   | **Branch** | `main` |
   | **Folder** | `/ (root)` |

5. Di bagian **Custom domain**, isi:

   ```
   tokopapuaonline.com
   ```

   ⚠️ Tulis **tanpa** `https://`, **tanpa** `www`, **tanpa** garis miring di akhir. Cukup `tokopapuaonline.com`.

6. Klik **Save**.
7. GitHub akan melakukan pemeriksaan DNS. Proses ini memakan **beberapa menit**:
   - Kalau DNS belum terbaca → muncul pesan kuning *"Domain's DNS record could not be retrieved"* — **jangan panik**, ini normal pada 30 menit pertama. Tunggu, lalu refresh. Lihat [Troubleshooting 7.1](#71--domains-dns-record-could-not-be-retrieved).
   - Kalau DNS sudah benar → muncul centang hijau di samping nama domain.
8. Setelah tersimpan, GitHub otomatis **membuatkan/memperbarui file `CNAME`** di root repository. Isinya tetap `tokopapuaonline.com`.

> **File `CNAME` sudah ada di paket ini**, jadi GitHub biasanya tinggal mencocokkan. Kalau GitHub menimpa isinya, itu tetap `tokopapuaonline.com` — tidak masalah.

---

## 5. Verifikasi DNS (nslookup / dig) & Waktu Propagasi

### 5.1 Verifikasi dengan `nslookup` (tersedia di Windows, macOS, Linux)

**Cek domain utama — harus muncul 4 alamat IP GitHub:**

```bash
nslookup tokopapuaonline.com
```

Yang diharapkan muncul di bagian **Address** (urutan bisa berbeda):

```
Address: 185.199.108.153
Address: 185.199.109.153
Address: 185.199.110.153
Address: 185.199.111.153
```

Kalau yang muncul hanya **1 IP** atau IP yang berbeda (misal IP parkir registrar), berarti masih ada A record lama yang belum dihapus, atau propagasi belum selesai.

**Cek subdomain `www`:**

```bash
nslookup www.tokopapuaonline.com
```

Harus menunjuk ke `<username>.github.io`.

### 5.2 Verifikasi dengan `dig` (macOS / Linux / Git Bash)

**Cek A record:**

```bash
dig tokopapuaonline.com +short
```

Output yang benar (4 baris):

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**Cek CNAME `www`:**

```bash
dig www.tokopapuaonline.com +short
```

Output yang benar:

```
<username>.github.io.
```

**Cek lewat server DNS publik (untuk memastikan sudah menyebar global):**

```bash
# Google DNS
dig @8.8.8.8 tokopapuaonline.com +short

# Cloudflare DNS
dig @1.1.1.1 tokopapuaonline.com +short
```

Kalau hasil dari Google/Cloudflare sudah benar tapi `dig` biasa belum, berarti cache di komputer Anda masih lama — coba:

```bash
# macOS
sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder

# Windows (Command Prompt sebagai Administrator)
ipconfig /flushdns

# Linux (systemd)
sudo resolvectl flush-caches
```

### 5.3 Cek lewat browser (cara paling mudah)

Buka alamat ini di browser — keduanya harus mengembalikan hasil:

- `https://tokopapuaonline.com/` → landing page **Toko Papua Online**
- `https://www.tokopapuaonline.com/` → akan otomatis dialihkan ke `https://tokopapuaonline.com/`

### 5.4 Estimasi waktu propagasi

| Skenario | Estimasi waktu |
|----------|----------------|
| Record baru, DNS registrar cepat (Cloudflare, Namecheap) | **5–30 menit** |
| Record baru, registrar lambat | **1–4 jam** |
| Ganti/turunkan TTL lama lalu ubah record | **1–24 jam** |
| Paling lama (kasus jarang, TTL besar) | **sampai 48 jam** |
| **Sertifikat HTTPS terbit** | **15 menit – 24 jam** (biasanya ±1 jam) |

> **Tips:** kalau setelah 24 jam masih belum jalan, jangan menunggu lebih lama — langsung cek [Troubleshooting](#7-troubleshooting). Hampir selalu ada satu record yang salah atau terlewat.

---

## 6. Mengaktifkan HTTPS (Enforce HTTPS)

Sertifikat HTTPS diterbitkan GitHub **otomatis dan gratis** (Let's Encrypt) setelah domain terverifikasi. Anda tidak perlu membeli apa pun.

1. Tunggu sampai DNS terbaca (Bagian 4 selesai, muncul centang hijau).
2. Buka **Settings → Pages** lagi.
3. Cari bagian **Enforce HTTPS** dan **centang** kotaknya.
4. Klik **Save** kalau diminta.

### Kalau kotak "Enforce HTTPS" tidak bisa dicentang (abu-abu)

Ini normal di awal. Penyebab dan solusinya:

| Penyebab | Solusi |
|----------|--------|
| Sertifikat belum selesai diterbitkan | **Tunggu 15 menit – 24 jam**, lalu refresh halaman. Biasanya sudah bisa dicek setelah ±1 jam |
| DNS belum sepenuhnya menyebar | Tunggu, lalu ulangi verifikasi `dig` (Bagian 5) |
| Proxy Cloudflare masih oranye | Set ke **DNS only** (abu-abu) untuk sementara |
| Baru saja mengubah DNS | Tunggu minimal 30 menit sebelum mencoba lagi |

### Setelah HTTPS aktif

| Kondisi | Hasil |
|---------|-------|
| `http://tokopapuaonline.com/` | Otomatis dialihkan ke `https://` |
| `https://tokopapuaonline.com/` | ✅ Situs tampil dengan gembok aman 🔒 |
| `http://www.tokopapuaonline.com/` | Dialihkan ke `https://tokopapuaonline.com/` |

---

## 7. Troubleshooting

### 7.1 ❌ "Domain's DNS record could not be retrieved"

Ini pesan yang **paling sering** muncul, dan hampir selalu bisa diperbaiki sendiri.

| Penyebab | Cara mengatasi |
|----------|----------------|
| **DNS belum menyebar** | Ini penyebab paling umum. Tunggu 30 menit – 1 jam, lalu klik **Save** lagi di Settings → Pages. Jangan diubah-ubah terus |
| **A record belum lengkap** | Harus ada **4** A record (`185.199.108.153` sampai `185.199.111.153`). Cek satu per satu dengan `dig tokopapuaonline.com +short` — harus keluar 4 baris |
| **Masih ada A record lama** | Hapus A record yang menunjuk ke IP hosting/parkir lama. Yang tersisa hanya boleh 4 IP GitHub |
| **CNAME `@` bentrok dengan A record** | DNS melarang CNAME sejajar dengan record lain. Hapus CNAME di `@`, sisakan 4 A record |
| **Proxy Cloudflare masih oranye** | Set **DNS only** (awan abu-abu) untuk keempat A record dan `www`. **Ini penyebab tersembunyi yang paling umum** |
| **Salah tulis domain** | Di kolom Custom domain: `tokopapuaonline.com` — tanpa `https://`, tanpa `www`, tanpa `/` di akhir |
| **`www` belum ada** | Tambahkan CNAME `www` → `<username>.github.io` |

**Urutan perbaikan yang disarankan:**

```bash
# 1. Pastikan 4 A record sudah benar
dig tokopapuaonline.com +short

# 2. Pastikan CNAME www sudah benar
dig www.tokopapuaonline.com +short
```

Kalau keduanya sudah benar tapi GitHub tetap menolak → tunggu 1 jam, lalu buka **Settings → Pages**, **hapus** isi kolom Custom domain, **Save**, lalu isi ulang `tokopapuaonline.com` dan **Save** lagi. Trik "hapus lalu isi ulang" ini memaksa GitHub memeriksa DNS dari awal dan biasanya langsung berhasil.

### 7.2 ❌ Sertifikat HTTPS belum terbit / "not secure"

| Penyebab | Cara mengatasi |
|----------|----------------|
| Sertifikat belum diproses | Tunggu sampai **24 jam**. GitHub menerbitkan sertifikat setelah DNS terverifikasi |
| **Enforce HTTPS** belum dicentang | Buka Settings → Pages → centang **Enforce HTTPS** |
| Proxy Cloudflare masih oranye | Set ke **DNS only**, tunggu 1 jam, lalu coba lagi |
| DNS baru saja berubah | Tunggu minimal 30 menit, lalu refresh halaman Settings → Pages |
| Sertifikat "nyangkut" | Hapus isi kolom Custom domain → **Save** → isi ulang → **Save**. GitHub akan menerbitkan sertifikat baru dari nol |
| Sudah pakai HTTPS tapi browser masih bilang tidak aman | Hard refresh (`Ctrl + F5` / `Cmd + Shift + R`) — sering hanya cache browser |
| Masih menunggu setelah 48 jam | Cek **Settings → Pages** apakah ada pesan error spesifik; kalau ada tulisan soal CAA, pastikan tidak ada record CAA di DNS yang melarang Let's Encrypt |

> **Cek status sertifikat:** buka `https://tokopapuaonline.com/` di browser → klik ikon gembok 🔒 → **Certificate** → lihat tanggal berlakunya. Kalau penerbitnya **Let's Encrypt** dan berlaku ±90 hari, berarti sertifikat GitHub sudah aktif.

### 7.3 ❌ Domain sudah diisi, tapi masih menampilkan 404

| Penyebab | Cara mengatasi |
|----------|----------------|
| File `CNAME` **hilang dari repository** | Buat ulang file `CNAME` berisi `tokopapuaonline.com` di root repository. Lihat [Bagian 9](#9-️-catatan-penting-file-cname-jangan-dihapus) |
| **GitHub Pages belum diaktifkan** | Settings → Pages → Source: **Deploy from a branch** → Branch `main` → Folder `/ (root)` → **Save** |
| **`index.html` tidak di root** | File `index.html` harus sejajar dengan `CNAME`, bukan di dalam sub-folder |
| Build belum selesai | Tunggu 1–2 menit, cek tab **Actions** untuk melihat progres build |
| Domain lama masih ter-*cache* | Coba mode incognito, atau hard refresh |
| Record DNS masih salah | Verifikasi ulang dengan `dig` (Bagian 5) |
| `www` menampilkan 404 tapi domain utama normal | Tambahkan CNAME `www` → `<username>.github.io` (lihat Bagian 2.2) |

> **Bedakan dua jenis 404:** 404 dari GitHub Pages (ada tulisan "There isn't a GitHub Pages site here") berarti masalah Pages/CNAME. 404 dari registrar (halaman iklan domain) berarti DNS belum mengarah ke GitHub sama sekali.

### 7.4 ❌ Domain utama jalan, tapi `www` tidak

1. Pastikan CNAME `www` → `<username>.github.io` sudah dibuat di DNS.
2. Verifikasi: `dig www.tokopapuaonline.com +short`.
3. Setelah jalan, GitHub akan otomatis mengalihkan `www.tokopapuaonline.com` → `tokopapuaonline.com`. Kalau ingin arah sebaliknya, atur di registrar lewat fitur redirect.
4. Kalau `www` masih 404, isi juga kolom Custom domain dengan bentuk `www.tokopapuaonline.com` → **Save** → lalu kembali ke `tokopapuaonline.com` → **Save**.

---

## 8. Cara Menghapus / Mengganti Domain

### 8.1 Mengganti ke domain lain

Misal pindah dari `tokopapuaonline.com` ke `tokopapuaonline.id`:

1. **Siapkan DNS domain baru:** buat 4 A record ke IP GitHub (`185.199.108.153` … `185.199.111.153`) dan CNAME `www` → `<username>.github.io`.
2. **GitHub:** buka **Settings → Pages** → hapus isi kolom Custom domain → **Save** → isi `tokopapuaonline.id` → **Save**.
3. **Ubah file `CNAME`** di repository: buka file `CNAME` → klik pensil ✏️ → ganti isinya menjadi `tokopapuaonline.id` → **Commit changes**.
4. **Perbarui tiga file SEO** supaya menunjuk domain baru:
   - `index.html` → `<link rel="canonical">` dan `<meta property="og:url">`
   - `sitemap.xml` → baris `<loc>`
   - `robots.txt` → baris `Sitemap:`

   Cara cepat (Linux/macOS/Git Bash), dijalankan di folder yang sama:

   ```bash
   sed -i 's|tokopapuaonline.com|tokopapuaonline.id|g' index.html sitemap.xml robots.txt CNAME
   ```

5. **Google Search Console:** tambahkan properti baru untuk domain baru, verifikasi, lalu submit `sitemap.xml` yang baru.

### 8.2 Menghapus domain kustom (kembali ke alamat GitHub Pages)

1. **Settings → Pages** → kosongkan kolom **Custom domain** → **Save**.
2. Hapus file **`CNAME`** dari root repository.
3. Situs kembali dapat diakses di `https://<username>.github.io/<nama-repo>/`.
4. Di DNS, hapus 4 A record dan CNAME `www` yang menunjuk ke GitHub — kalau dibiarkan, domain Anda akan mengarah ke situs yang tidak ada lagi.

> **Catatan:** setelah menghapus domain kustom, jangan lupa kembalikan juga `canonical`, `og:url`, `sitemap.xml`, dan `robots.txt` ke alamat GitHub Pages agar tidak menunjuk ke domain mati.

---

## 9. ⚠️ Catatan Penting: File `CNAME` Jangan Dihapus

File **`CNAME`** di root repository adalah **satu-satunya penanda** yang memberi tahu GitHub Pages bahwa situs Anda dilayani di `tokopapuaonline.com`.

**Isi file ini cukup satu baris:**

```
tokopapuaonline.com
```

### Aturan yang wajib dipatuhi

| Aturan | Alasan |
|--------|--------|
| ❌ **JANGAN hapus file `CNAME`** | Tanpa file ini, GitHub tidak tahu domain mana yang harus dilayani. Domain Anda akan menampilkan **404** atau kembali ke alamat `github.io` |
| ❌ **Jangan ubah namanya** | Harus persis `CNAME` — huruf besar semua, tanpa ekstensi. Bukan `cname`, bukan `CNAME.txt` |
| ❌ **Jangan pindahkan ke sub-folder** | Harus di **root** repository, sejajar dengan `index.html` |
| ✅ **Isinya satu baris saja** | `tokopapuaonline.com` — tanpa `https://`, tanpa `www`, tanpa `/` di akhir |
| ✅ **Pastikan ikut ter-commit** | Kalau upload lewat web GitHub, jangan lupa file ini ada di daftar sebelum klik **Commit changes** |

### Kenapa file ini mudah hilang?

- Saat **upload ulang seluruh paket** lewat drag & drop, orang sering lupa menyertakan `CNAME` karena namanya tanpa ekstensi dan bisa tersembunyi di sistem operasi tertentu.
- Saat **mengganti file secara massal**, `CNAME` kadang ikut terhapus.
- Saat **membuat repository baru** dan hanya menyalin `index.html`.

### Kalau `CNAME` sudah terlanjur terhapus

Perbaikannya cepat:

**Lewat web GitHub:**
1. Buka repository → **Add file** → **Create new file**.
2. Beri nama: `CNAME`
3. Isi satu baris: `tokopapuaonline.com`
4. Klik **Commit changes**.
5. Tunggu 1–2 menit, lalu buka kembali domain Anda.

**Lewat terminal:**

```bash
printf 'tokopapuaonline.com\n' > CNAME
git add CNAME
git commit -m "Kembalikan file CNAME untuk domain kustom"
git push
```

**Cek cepat file ini masih ada:**
```bash
cat CNAME
# Output yang benar: tokopapuaonline.com
```

> ⚠️ **Perhatian:** GitHub juga otomatis menulis ulang file `CNAME` setiap kali Anda menyimpan Custom domain di Settings → Pages. Jadi kalau Anda mengubahnya manual, pastikan isinya tetap sama dengan yang ada di pengaturan GitHub — kalau berbeda, GitHub akan menimpanya.

---

## 10. Checklist Akhir

### DNS (di registrar)

- [ ] 4 **A record** `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- [ ] 1 **CNAME** `www` → `<username>.github.io`
- [ ] A record / CNAME lama yang menunjuk ke hosting atau parkir **sudah dihapus**
- [ ] Tidak ada **CNAME di `@`** (bentrok dengan A record)
- [ ] Kalau pakai **Cloudflare**: Proxy status = **DNS only** (awan abu-abu)
- [ ] Fitur **domain parking / forwarding** di registrar sudah dimatikan

### GitHub

- [ ] **Settings → Pages → Custom domain** = `tokopapuaonline.com`
- [ ] **Source** = Deploy from a branch · Branch `main` · Folder `/ (root)`
- [ ] File **`CNAME`** ada di root repository dan isinya `tokopapuaonline.com`
- [ ] **Enforce HTTPS** sudah dicentang
- [ ] Sertifikat HTTPS sudah terbit (ikon gembok 🔒 di browser)

### SEO

- [ ] `index.html` → `<link rel="canonical">` = `https://tokopapuaonline.com/`
- [ ] `index.html` → `<meta property="og:url">` = `https://tokopapuaonline.com/`
- [ ] `sitemap.xml` → `<loc>` = `https://tokopapuaonline.com/`
- [ ] `robots.txt` → `Sitemap: https://tokopapuaonline.com/sitemap.xml`
- [ ] **Tidak ada sisa placeholder** `USERNAME` atau `NAMA-REPO` — cek dengan:
  ```bash
  grep -rn "USERNAME\|NAMA-REPO" index.html sitemap.xml robots.txt
  # Output yang benar: tidak ada apa-apa
  ```
- [ ] Sitemap sudah disubmit ulang di Google Search Console untuk properti domain baru

### Hasil akhir yang diharapkan

| URL | Hasil |
|-----|-------|
| `https://tokopapuaonline.com/` | ✅ Landing page Toko Papua Online, gembok aman 🔒 |
| `https://www.tokopapuaonline.com/` | ✅ Dialihkan ke `https://tokopapuaonline.com/` |
| `http://tokopapuaonline.com/` | ✅ Dialihkan ke `https://` |
| `https://tokopapuaonline.com/sitemap.xml` | ✅ XML valid, `<loc>` memuat domain baru |
| `https://tokopapuaonline.com/robots.txt` | ✅ `Sitemap:` menunjuk domain baru |

---

Selamat! Landing page **Toko Papua Online** Anda sekarang berjalan di domain sendiri: **tokopapuaonline.com**.

Kalau di kemudian hari muncul masalah DNS atau HTTPS lagi, mulai dari **Bagian 5 (Verifikasi)** — hampir semua jawabannya ada di situ.
