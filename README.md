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
| `robots.txt` | Mengizinkan semua crawler + baris `Sitemap:` menunjuk ke `sitemap.xml` (alamat GitHub Pages sudah terisi) |
| `sitemap.xml` | Peta situs (Sitemap Protocol 0.9, UTF-8) berisi URL halaman toko (alamat GitHub Pages sudah terisi) |
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
| Footer | **Lanskap: 3 kolom berjajar ke samping** (lihat **Bagian 10**) | 3 kolom sejajar, tema gelap |

Diverifikasi pada **390 × 844** (mobile) dan **1280 × 900** (desktop), tanpa
overflow horizontal pada keduanya.

**Komponen & interaksi**

- **Carousel banner** — tombol sebelumnya/berikutnya, dot indikator, rotasi otomatis
  (dinonaktifkan bila pengguna mengaktifkan *prefers-reduced-motion*).
- **Filter kategori** — Semua / Promo / Terlaris / Baru.
- **Pencarian produk** — menyaring kartu secara langsung berdasarkan judul dan kategori.
- **Kartu produk** — sampul, judul (maksimal 3 baris), harga, tombol **Beli**
  yang membuka halaman checkout di tab baru (`target="_blank"`, `rel="noopener noreferrer"`).
- **Tombol Bagikan (Share) pada SETIAP kartu produk** — ikon bagikan di samping tombol
  Beli; membuka menu berisi **WhatsApp**, **Facebook**, **X/Twitter**, **Telegram**, dan
  **Salin tautan**. Tautan yang dibagikan menuju halaman toko beserta judul produknya
  (lihat **Bagian 8**).
- **Modal detail produk** — sampul besar, deskripsi, rincian harga, tombol
  *Tambah ke Keranjang* dan *Beli Sekarang*.
- **Keranjang** — panel samping (drawer) dengan penambahan/pengurangan jumlah,
  hapus item, subtotal, dan tombol lanjut ke pembelian.
- **Notifikasi (toast)** — umpan balik saat produk masuk keranjang.
- **Chatbot (widget chat melayang)** — tombol bulat di pojok kanan bawah yang membuka
  panel percakapan berisi panduan **cara membeli**, **cara mencari buku**, **cara memesan**,
  format berkas & cara unduh, metode pembayaran, serta kontak admin. Dilengkapi tombol
  pilihan cepat dan dapat menjawab pertanyaan bebas dengan pencocokan kata kunci —
  **tanpa API eksternal, tanpa kunci API, tanpa layanan pihak ketiga**. Chatbot juga
  membalas **ucapan terima kasih** dengan ramah dan menutup alur bantuan (cara membeli /
  mencari / memesan) memakai kalimat terima kasih (lihat **Bagian 9**).
- **Footer lanskap di mobile** — di layar HP kolom footer (*Tentang*, *Jelajahi*, *Bantuan*)
  **berjajar ke samping** dalam tiga kolom, bukan bertumpuk vertikal. Padding bawah footer
  dinaikkan agar baris hak cipta tidak tertutup bottom tab bar maupun tombol chat melayang.
  Tampilan desktop tidak berubah (lihat **Bagian 10**).
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

## 7. robots.txt & sitemap.xml (SEO)

Paket ini menyertakan dua berkas untuk mesin pencari:

| Berkas | Fungsi | Isi |
|---|---|---|
| `robots.txt` | Memberi tahu crawler bahwa seluruh situs boleh diindeks, sekaligus menunjukkan lokasi sitemap | `User-agent: *` · `Allow: /` · satu baris `Sitemap:` |
| `sitemap.xml` | Peta situs (Sitemap Protocol 0.9, UTF-8) berisi URL halaman toko utama | satu `<url>` dengan `<loc>`, `<lastmod>`, `<changefreq>`, `<priority>` |

**Alamat situs sudah terisi — tidak ada yang perlu diganti manual.** Kedua berkas sudah
memuat URL GitHub Pages yang sebenarnya, jadi paket ini siap diunggah apa adanya:

```
robots.txt   ->  Sitemap: https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/sitemap.xml
sitemap.xml  ->  <loc>https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/</loc>
```

**Bila nama repositori diubah** (atau situs dipindahkan ke alamat lain), perbarui alamat di
**kedua** berkas agar tetap sama persis. Cara mengeditnya langsung di GitHub: buka berkasnya
→ klik ikon **pensil (Edit this file)** → ubah teksnya → **Commit changes**. Perhatikan huruf
besar/kecil: nama repositori ini ditulis persis `Toko-Online-Papua-E-Book`.

**Cara memeriksa:** buka `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/robots.txt`
dan `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/sitemap.xml` di browser —
keduanya harus tampil sebagai teks/XML, bukan halaman Not Found. Langkah lengkapnya ada di
**Bagian 6.6** pada berkas `panduan-upload-github.md`.

> Kedua berkas ini **tidak berpengaruh** pada tampilan halaman toko. Halaman tetap berfungsi
> penuh; alamat di dalamnya hanya dipakai agar mesin pencari mengenali situs Anda dengan benar.

---

## 8. Tombol Bagikan (Share) per Produk

Setiap kartu produk memiliki tombol bagikan (ikon bagikan) di samping tombol Beli.
Tombol ini ada pada **semua** produk tanpa konfigurasi tambahan — begitu produk baru
ditambahkan ke blok `PRODUCTS`, tombol bagikannya ikut dibuat otomatis.

### Media yang tersedia

| Pilihan | Cara kerja |
|---|---|
| **WhatsApp** | Membuka `wa.me` berisi teks produk + tautan halaman toko |
| **Facebook** | Membuka jendela berbagi Facebook (`facebook.com/sharer`) dengan tautan halaman |
| **X / Twitter** | Membuka jendela tulis X (`twitter.com/intent/tweet`) berisi judul produk + tautan |
| **Telegram** | Membuka `t.me/share` berisi tautan + judul produk |
| **Salin tautan** | Menyalin judul produk + tautan halaman ke papan klip, lalu menampilkan notifikasi *"Tautan produk disalin"* |

### Isi tautan yang dibagikan

Semua pilihan di atas membagikan **URL halaman toko + nama produk**, sehingga penerima
langsung tahu produk apa yang sedang dibagikan. Contoh teks yang terkirim:

```
E-Book Belanda di Irian Jaya: Amtenar di Masa Penuh Gejolak 1945-1962 (Pim Schoorl - KITLV) - Rp 50.000

Beli e-book ini di Toko Papua Online:
https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/
```

### Menutup menu bagikan

Menu dapat ditutup dengan tiga cara: klik area gelap di luar panel, tombol **×** di
pojok panel, atau menekan tombol **Esc**. Menu ini berdiri sendiri dan **tidak mengganggu**
tombol Beli, keranjang, maupun modal detail produk.

### Mengubah URL yang dibagikan

URL halaman toko yang dipakai tombol bagikan diatur pada satu baris di dalam
`index.html`:

```js
var PAGE_URL = 'https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/';
```

Bila nama repositori berubah, samakan nilai di baris tersebut dengan alamat situs yang
baru. Teks ajakan ("Beli e-book ini di Toko Papua Online") diatur pada fungsi
`shareTextFor` tepat di bawahnya.

> Tombol bagikan **tidak menambah berkas baru** dan tidak memuat pustaka eksternal —
> seluruh ikon memakai inline SVG sprite yang sudah ada.

**Verifikasi:** buka situs live → klik tombol bagikan pada salah satu kartu → panel
muncul dengan lima pilihan → klik **Salin tautan** → notifikasi muncul. Pastikan juga
tombol **Beli** tetap membuka halaman checkout seperti biasa.

---

## 9. Chatbot (Widget Chat Melayang)

Halaman toko memiliki **asisten toko** berupa widget chat melayang di pojok kanan bawah.
Widget ini berjalan **sepenuhnya di dalam `index.html`**: tidak ada API eksternal, tidak
ada kunci API, dan tidak ada layanan pihak ketiga — sehingga tidak ada yang bisa gagal
karena jaringan atau biaya langganan.

### Cara membuka & menutup

| Aksi | Cara |
|---|---|
| Buka | Klik tombol bulat (ikon balon percakapan) di **pojok kanan bawah** |
| Tutup | Klik tombol **×** di kepala panel, tekan tombol **Esc**, atau klik di luar area chat |
| Tombol yang sama | Setelah dibuka, tombol bulat berubah menjadi ikon **×** — klik sekali lagi untuk menutup |

Panel chat **tidak menutupi** tombol Beli/Bagikan pada kartu produk maupun bottom tab bar
di HP: tombolnya diletakkan di atas tab bar (mobile) dan di sudut kanan bawah (desktop).

### Cakupan jawaban

Basis pengetahuan (`CHAT_KB`) berisi 14 topik yang mencakup seluruh kebutuhan yang diminta:

| Topik | Isi jawaban |
|---|---|
| **Cara membeli** | Pilih produk → klik **Beli** → diarahkan ke halaman **checkout OrderHero** → isi data → bayar → terima tautan unduhan PDF. Termasuk alur lewat keranjang dan catatan biaya transaksi. |
| **Cara mencari buku** | Kolom pencarian di header, filter kategori (Semua/Promo/Terlaris/Baru), katalog produk, tombol **Produk** di bilah bawah HP, dan klik kartu untuk deskripsi. |
| **Cara memesan** | Langkah pemesanan buku yang sudah tersedia, pesanan buku yang **belum tersedia**, pesanan khusus, pembelian **jumlah banyak/institusi** (harga khusus + invoice), serta **kontak admin**. |
| **Format berkas** | Semua produk e-book **PDF**. |
| **Cara mengunduh** | Tautan unduhan dikirim ke email setelah pembayaran terkonfirmasi. |
| **Bisa dibaca di HP** | Ya — PDF dapat dibuka di Android/iPhone maupun komputer. |
| **Metode pembayaran** | Pilihan tampil di halaman checkout OrderHero. |
| **Tautan unduhan belum diterima** | Cek folder Spam/Promosi, pastikan email benar, tunggu 5–10 menit, lalu hubungi admin dengan nomor pesanan + bukti pembayaran. |
| **Hubungi admin** | Mengarahkan ke bagian **Kontak & dukungan** di halaman toko. |
| **Harga, Promo, Keamanan transaksi, Produk tersedia, Mulai (sapaan)** | Jawaban pelengkap yang ikut memperkaya percakapan. |

### Tombol pilihan cepat (quick replies)

Di bawah area percakapan selalu tersedia lima tombol: **Cara membeli**, **Cara mencari buku**,
**Cara memesan**, **Metode pembayaran**, dan **Hubungi admin**. Selain itu, setiap jawaban
bot menampilkan **saran lanjutan** (mis. setelah “Cara membeli” muncul *Cara mencari buku*,
*Metode pembayaran*, *Cara mengunduh*, *Hubungi admin*), sehingga pengguna bisa menelusuri
seluruh topik **tanpa mengetik sama sekali**.

### Pertanyaan bebas & jawaban cadangan

Pengguna juga bisa mengetik pertanyaan sendiri. Pertanyaan tersebut dicocokkan dengan
kata kunci pada `CHAT_KB` memakai skor sederhana (frasa panjang bernilai lebih tinggi,
kata pendek hanya cocok sebagai kata utuh). Bila tidak ada topik yang cukup cocok,
chatbot menampilkan **jawaban cadangan** yang menyebutkan topik yang tersedia dan
mengarahkan pengguna ke **kontak admin** — bukan balasan kosong atau diam.

### Ucapan terima kasih

Chatbot mengenali ucapan terima kasih dan membalasnya dengan ramah — **tanpa mengubah
topik atau jawaban lain yang sudah ada**.

| Bagian | Nilai |
|---|---|
| Pemicu (`CHAT_THANKS_KEYS`) | `terima kasih`, `terima kasih banyak`, `terimakasih`, `makasih`, `mksh`, `thanks`, `thank you`, `thankyou`, `thx`, `tks`, `tq`, `syukron`, `syukran`, `jazakallah`, `sudah dibantu`, `sudah membantu`, `sangat membantu`, `membantu sekali`, `sangat terbantu`, `sudah cukup`, `cukup jelas`, `jelas sekali`, `oke terima kasih`, `ok terima kasih`, `baik terima kasih`, `terima kasih ya`, `oke thanks`, `oke makasih`, `mantap terima kasih` — **32 kata kunci** |
| Balasan (`chatThanksBody()`) | Menyebut **Toko Papua Online**, berterima kasih, mengajak menghubungi admin bila masih ada pertanyaan, dan menyertakan tautan halaman toko |
| Saran lanjutan (`CHAT_THANKS_FOLLOW`) | **Cara membeli**, **Cara mencari buku**, **Cara memesan**, **Hubungi admin** |
| Penutup alur bantuan (`CHAT_THANKS_CLOSE`) | Kalimat terima kasih yang ditambahkan di akhir jawaban **Cara membeli**, **Cara mencari buku**, dan **Cara memesan** |

**Aturan urutan:** ucapan terima kasih dicek **setelah** pencocokan topik. Jadi pertanyaan
yang kebetulan memuat kata “terima kasih” tetap dijawab sesuai topiknya, sedangkan sapaan
singkat seperti *“terima kasih”* saja tidak lagi jatuh ke jawaban cadangan.

**Mengubah teksnya:** sunting bagian berikut di dalam `index.html`.

```js
var CHAT_THANKS_KEYS = ['terima kasih', 'makasih', 'thanks', ...];  // daftar pemicu
var CHAT_THANKS_FOLLOW = ['beli', 'cari', 'pesan', 'admin'];        // saran lanjutan
var CHAT_THANKS_CLOSE = '<br><br>Terima kasih telah memilih <b>Toko Papua Online</b> ...';
function chatThanksBody() { return '<b>Terima kasih banyak!</b> ...'; }
```

- **Menambah pemicu** → tambahkan string baru ke `CHAT_THANKS_KEYS`.
- **Mengubah kalimat balasan** → sunting isi `chatThanksBody()`.
- **Mengubah atau menghapus penutup** pada alur bantuan → sunting `CHAT_THANKS_CLOSE`
  (isi `''` bila tidak ingin ada penutup).

### Mengubah daftar pertanyaan/jawaban

Semua jawaban berada pada **satu objek** bernama `CHAT_KB` di dalam `index.html`. Setiap
entri berbentuk:

```js
{
  id: 'beli', label: 'Cara membeli',
  keys: ['cara membeli', 'cara beli', 'beli', 'checkout', ...],
  follow: ['cari', 'bayar', 'unduh', 'admin'],
  answer: '<b>Cara membeli buku</b><br>1. Buka halaman toko ... '
}
```

| Bagian | Fungsinya |
|---|---|
| `id` | Nama unik topik (dipakai oleh `follow`) |
| `label` | Teks tombol saran lanjutan + dicocokkan langsung bila pengguna klik tombol itu |
| `keys` | Daftar kata kunci/frasa yang memicu jawaban ini |
| `answer` | Isi jawaban (boleh berisi HTML sederhana: `<b>`, `<br>`, `&bull;`, tautan) |
| `build` | *Opsional* — fungsi yang membangun jawaban saat dipanggil (dipakai topik **Harga** dan **Produk tersedia** agar daftar produk otomatis ikut diperbarui) |
| `follow` | Daftar `id` yang muncul sebagai tombol saran setelah jawaban |

**Menambah topik baru:** salin satu entri, ubah `id`, `label`, `keys`, dan `answer`.
Tombol pilihan cepat tetap (bawah) diatur di array `CHAT_QUICK`, jawaban cadangan di
objek `CHAT_FALLBACK`, dan ucapan terima kasih di `CHAT_THANKS_KEYS` + `chatThanksBody()`.


**Menambah kontak admin langsung:** isi dua baris berikut agar jawaban “Hubungi admin”
memuat tautan siap klik (kosongkan kembali dengan `''` bila tidak ingin ditampilkan):

```js
var CHAT_WA_ADMIN = '62812xxxxxxx';   // nomor WhatsApp admin
var CHAT_MAIL_ADMIN = 'admin@toko.id'; // email admin
```

**Catatan penting:** jangan mengetikkan garis miring `\` atau tanda kutip `'` di dalam
`answer` tanpa di-escape (`\'`), karena dapat membuat JavaScript gagal diurai.

### Cara menguji chatbot

1. Buka halaman → klik tombol bulat di pojok kanan bawah.
2. Sambutan bot muncul, lima tombol pilihan cepat tampil di bawah.
3. Klik **Cara membeli** → jawaban enam langkah muncul beserta tautan halaman toko dan
tautan checkout.
4. Klik **Cara mencari buku**, **Cara memesan**, **Metode pembayaran**, **Hubungi admin** —
masing-masing harus menjawab topiknya.
5. Ketik pertanyaan bebas, mis. *"bisa dibaca di HP?"* atau *"berapa harganya?"*.
6. Ketik pertanyaan di luar topik, mis. *"resep rendang"* → jawaban cadangan + arahan ke admin.
7. Ketik **terima kasih** (coba juga *makasih*, *thanks*, *tq*, *syukron*) → balasan terima
   kasih yang menyebut Toko Papua Online, memuat tautan halaman toko, dan menampilkan empat
   tombol saran lanjutan (Cara membeli / Cara mencari buku / Cara memesan / Hubungi admin).
8. Klik **Cara membeli** → perhatikan jawaban ditutup dengan kalimat terima kasih; ulangi
   untuk **Cara mencari buku** dan **Cara memesan**.
9. Tutup dengan **×**, lalu buka lagi dan tutup dengan **Esc** dan dengan klik di luar panel.
10. Di HP, pastikan widget tidak menutupi bottom tab bar dan tombol Beli/Bagikan.

> Chatbot **tidak menambah berkas baru** dan tidak memuat pustaka eksternal — seluruh
> ikon memakai inline SVG sprite yang sudah ada.

---

## 10. Footer Lanskap (Khusus Mobile)

Pada layar HP, kolom-kolom footer **berjajar ke samping (lanskap)** — bukan bertumpuk
vertikal satu per satu. Tata letak ini di-scope ke `@media (max-width:767px)` sehingga
**tampilan desktop sama sekali tidak berubah**.

| | Mobile (≤ 767 px) | Desktop (≥ 768 px) |
|---|---|---|
| Kolom | **3 kolom berjajar ke samping** | 3 kolom sejajar (tidak berubah) |
| Lebar kolom | `1.15fr 1fr 1fr` (≈ 125 / 109 / 109 px pada 390 px) | `1.6fr 1fr 1fr` (≈ 468 / 292 / 292 px pada 1280 px) |
| Jarak antar kolom (`gap`) | 12 px | 40 px |
| Padding footer | `24px 12px 140px` | `44px 0 34px` |
| Ukuran teks kolom | 11 px | 13 px |
| Baris hak cipta | Tersusun **vertikal** (2 baris) | Satu baris, kiri–kanan |

### Cara kerja

Tata letak lama di mobile adalah `grid-template-columns:1fr` — satu kolom, sehingga blok
*Tentang*, *Jelajahi*, dan *Bantuan* bertumpuk dari atas ke bawah dan footer menjadi sangat
tinggi. Aturan baru menggantinya dengan **tiga kolom berjajar**:

```css
@media (max-width:767px){
  .site-footer{padding:24px 12px calc(140px + env(safe-area-inset-bottom))}
  .foot-grid{
    grid-template-columns:minmax(0,1.15fr) minmax(0,1fr) minmax(0,1fr);
    gap:12px;
    align-items:start;
  }
  /* … */
}
```

`minmax(0, …)` dipakai agar kolom **boleh mengecil di bawah lebar kontennya** — tanpa ini,
kata terpanjang (mis. "komprehensif") akan memaksa kolom melebar dan memicu scroll
horizontal. Ditambah `overflow-wrap:break-word` pada tiap blok sebagai pengaman.

### Jarak aman dari elemen tetap

Padding bawah footer di mobile dinaikkan menjadi **140 px** (sebelumnya 84 px) supaya baris
hak cipta berada jauh di atas dua elemen tetap:

- **Bottom tab bar** (tinggi 60 px, menempel di dasar layar)
- **Tombol chat melayang** (54 × 54 px, `bottom:74px` dari dasar)

Hasil pengukuran setelah perubahan: jarak baris hak cipta ke tab bar **79 px**, dan ke
tombol chat **12 px** pada lebar 360 / 390 / 430 px. Nilai `env(safe-area-inset-bottom)`
ditambahkan agar aman di iPhone dengan *home indicator*.

### Mengubahnya

Semua aturan ada di satu blok `@media (max-width:767px)` di dalam `<style>`, tepat
sebelum komentar `/* ============ TABBAR (mobile) ============ */`:

| Yang ingin diubah | Ubah baris |
|---|---|
| Jumlah kolom | `grid-template-columns:minmax(0,1.15fr) minmax(0,1fr) minmax(0,1fr)` — tambah/kurangi angka `fr` |
| Lebar kolom pertama | Angka `1.15fr` |
| Jarak antar kolom | `gap:12px` |
| Jarak aman bawah | `padding:24px 12px calc(140px + env(safe-area-inset-bottom))` |
| Ukuran teks link | `.foot-col a,.foot-col span{font-size:11px}` |

> ⚠️ Bila menambah kolom, **kurangi** ukuran `fr` tiap kolom (mis. `1fr 1fr 1fr 1fr`) dan
turunkan `font-size` ke ± 10 px — pada 360 px, empat kolom hanya memberi ± 82 px per
kolom.

### Cara menguji

1. Buka situs di HP, atau di browser desktop tekan **F12** → mode perangkat → **390 × 844**.
2. Gulir ke paling bawah. Ketiga blok (*Tentang*, *Jelajahi*, *Bantuan*) harus tampak
   **berdampingan ke samping**, bukan bertumpuk.
3. Periksa **tidak ada scroll horizontal** (halaman tidak bisa digeser ke kiri/kanan).
4. Pastikan tidak ada kata yang terpotong; kata terpanjang ("komprehensif") harus utuh.
5. Pastikan baris hak cipta **tidak tertutup** bottom tab bar maupun tombol chat melayang.
6. Perbesar ke **360 px** dan **430 px** — tata letak harus tetap tiga kolom dan tetap rapi.
7. Beralih ke **1280 × 900** — footer harus **persis sama** seperti sebelumnya
   (kolom `1.6fr 1fr 1fr`, gap 40 px, teks 13 px).

> Footer tidak menambah berkas baru dan tidak memuat pustaka eksternal — hanya CSS di
> dalam `index.html`.

---

## 11. Langkah Selanjutnya — Panduan Upload Lengkap

Panduan upload ke GitHub Pages yang **sangat rinci** ada di **`panduan-upload-github.md`**.
Isinya 9 bagian:

| Bagian | Isi |
|---|---|
| 1 | **Persiapan & ekstrak ZIP** — cara ekstrak di Windows / macOS / Android, struktur folder yang benar, cara memastikan `.nojekyll` tidak hilang |
| 2 | **Akun GitHub & repositori** — daftar akun, nama repo yang disarankan, wajib **Public**, jangan centang README/.gitignore/license |
| 3 | **Upload berkas** — (a) lewat web GitHub: *Add file ▾ → Upload files*, drag & drop isi folder + memastikan folder `images/` ikut; (b) lewat **GitHub Desktop**: install → sign in → add local repository → publish → push |
| 4 | **Commit & periksa hasil** — memastikan 11 berkas + folder `images/` tampil di repositori |
| 5 | **Aktifkan GitHub Pages** — *Settings → Pages → Source: Deploy from a branch → Branch `main` → Folder `/ (root)` → Save*, lalu cara menemukan URL situs |
| 6 | **Tunggu & verifikasi situs live** — 1–2 menit, cek gambar tampil, cek tombol **Beli** mengarah ke link checkout, cek **tombol Bagikan** membuka lima pilihan media & salin tautan (**Bagian 6.7**), cek **chatbot** membuka/menutup & menjawab (**Bagian 6.8**), cek tampilan mobile (termasuk **footer lanskap**, Bagian 6.10) & desktop, dan cek `robots.txt` + `sitemap.xml` **Bagian 6.6** |
| 7 | **Update di kemudian hari** — edit langsung di GitHub atau unggah ulang, mengganti gambar, menambah produk, memastikan perubahan terbit |
| 8 | **Troubleshooting lengkap** — 404, gambar tidak muncul, CSS/JS tidak jalan, tampil sebagai kode mentah, `.nojekyll` hilang, repo Private, salah folder root, cache browser, mode incognito, `robots.txt`/`sitemap.xml`, tombol Bagikan, **chatbot**, dan **footer lanskap mobile** |
| 9 | **FAQ & daftar periksa** — pertanyaan umum + checklist langkah demi langkah |

### Ringkasan alur upload

1. Ekstrak ZIP ke sebuah folder.
2. Buat repositori GitHub baru berstatus **Public** (kosong, tanpa README).
3. **Add file ▾ → Upload files** → seret seluruh **isi** folder → **Commit changes**.
4. **Settings → Pages** → *Deploy from a branch* → Branch `main` → Folder `/ (root)` → **Save**.
5. Tunggu 1–2 menit, situs aktif di `https://tokopapuaonline.github.io/Toko-Online-Papua-E-Book/`.
6. Uji tombol **Beli** (harus membuka halaman checkout) dan tombol **Bagikan** (lima pilihan media + salin tautan).
7. Uji **chatbot**: klik tombol bulat di pojok kanan bawah, coba kelima tombol pilihan cepat, lalu tutup dengan **Esc** atau klik di luar panel.
8. Uji **footer lanskap** di HP: gulir ke bawah — kolom footer harus berjajar ke samping, tanpa scroll horizontal, dan tidak tertutup bottom tab bar.

> **Paling sering salah:** pastikan `index.html` berada di tingkat paling atas repositori
> (sejajar dengan folder `images/`), bukan di dalam subfolder.
