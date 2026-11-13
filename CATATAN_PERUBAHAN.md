# Catatan perubahan v7 -> v11

## Sudah diterapkan
- SEO/berbagi: canonical, og:url, og:image absolut + ukuran + alt, twitter:image, JSON-LD Organization, sitemap.xml, robots.txt
- bmc.html: metadata unik, judul halaman kini <h1> (gaya tetap sama)
- Hero: CTA utama "Minta penawaran" (-> #pemesanan)
- Form penawaran: tambah Kota dan Jumlah unit, ikut masuk ke pesan WhatsApp
- Isi paket: catatan kelengkapan perangkat (tablet, aki, kabel) dirinci di penawaran
- Aksesibilitas: label menu dinamis (Buka/Tutup navigasi), tutup dengan Esc, skip link, fokus pindah ke pemutar video
- Kode: satu listener menu (sebelumnya dua), hapus kode mati (--x)

## WAJIB DIISI SENDIRI (tidak saya karang)
1. (SELESAI di v11) Domain kerabat-teknik.wahyudintamrin.com sudah dipasang di index.html, bmc.html, sitemap.xml, robots.txt
2. Isi paket: tulis tegas apakah tablet, aki, kabel termasuk (lihat komentar TODO di index.html)
3. Email bisnis, alamat/kota, jam layanan, status legal (belum ditambahkan karena datanya tidak ada)

## Belum dikerjakan (butuh keputusan/aset Anda)
Harga/kisaran, spesifikasi, testimoni/bukti uji coba, foto produk baru, FAQ, kebijakan simulator publik vs bonus, domain simulator, konsistensi klaim purna jual vs BMC.

---
# Tambahan Minggu 2 (v9)
## Sudah diterapkan
- Harga Rp 5.000.000 per unit: kartu harga di section Produk, paket, tabel spesifikasi, FAQ, dan JSON-LD Product
- Section baru "Spesifikasi" (tabel; susun bertumpuk di mobile) berisi hanya data yang terlihat di situs/foto produk
- Section baru "FAQ" (6 pertanyaan, <details> tanpa JS) + JSON-LD FAQPage yang teksnya sama
- "Cara memesan" dipindah naik, sebelum katalog; link FAQ ditambahkan di navigasi kedua halaman
## Perlu dipastikan
- "per unit": saya asumsikan harga per unit trainer. Ubah jika berbeda (index.html, FAQ, JSON-LD)
- Ongkos kirim: ditulis "dikonfirmasi dalam penawaran" (netral). Ganti jika sudah ada kebijakan pasti
## Masih menunggu data/aset (lihat komentar TODO di index.html)
Dimensi, berat, kebutuhan daya, garansi, estimasi pengiriman; FAQ garansi/purna jual/termin; testimoni;
foto produk baru; caption/transkrip video (butuh teks narasi video); pindah domain simulator.

---
# Tambahan v10 (Bulan 2, bagian yang tidak butuh data)
## Sudah diterapkan
- CSS inline dari kedua halaman digabung ke satu `styles.css` (di-cache lintas halaman). Diverifikasi identik piksel di 6 tampilan.
  Saat mengubah styles.css, naikkan angka `?v=10` di kedua HTML agar cache browser ikut diperbarui.
- Font Barlow dan Barlow Condensed dihosting sendiri di `fonts/` (woff2 subset latin, lisensi OFL disertakan), dengan preload untuk 3 font utama.
  Tidak ada lagi permintaan ke Google Fonts. Sebelumnya font sebenarnya tidak termuat saat offline/jaringan terblokir.
- Footer: © 2026. Catatan privasi singkat di form penawaran.
- Aksesibilitas: tautan yang membuka tab baru diberi teks untuk pembaca layar; teks status skema tidak lagi bergantung warna ("merah muda").
## Tidak dikerjakan
- Pembersihan aturan CSS yang saling menimpa (tambalan versi lama): berisiko mengubah tampilan, sebaiknya dilakukan bertahap dengan uji visual.
- Analytics: butuh akun/layanan pilihan Anda (mis. Plausible/Umami).
- Thumbnail YouTube masih diambil dari img.youtube.com (satu-satunya request pihak ketiga yang tersisa).

---
# v11
- Domain kerabat-teknik.wahyudintamrin.com dipasang di canonical, og:url, og:image, twitter:image, JSON-LD, sitemap.xml, robots.txt
- Foto produk dan poster video dikonversi ke WebP (352 KB -> 198 KB); referensi di index.html diperbarui, JPG lama dihapus
  (og-image.jpg tetap JPG karena dibutuhkan pratinjau media sosial)
- Video sudah dalam format yang bisa diputar sambil mengunduh, tidak diubah
- Diuji lewat server HTTP: tidak ada request gagal dan tidak ada peringatan preload. Membuka langsung lewat file:// akan menampilkan
  peringatan preload font; itu normal dan tidak terjadi saat di-hosting.
## Saat deploy
- Unggah SELURUH isi folder (termasuk styles.css, fonts/, images/, sitemap.xml, robots.txt)
- Pastikan situs dilayani lewat HTTPS agar canonical dan og:url (https) sesuai
- Setelah online, cek pratinjau tautan di WhatsApp dan validasi JSON-LD di Rich Results Test

---
# v12
Hasil audit otomatis axe-core (WCAG 2.2 AA + best practice) pada index dan bmc, tema terang/gelap, desktop/mobile: sebelum 2 catatan (moderate), sesudah 0 pelanggaran. Tidak ada masalah kontras warna.
- index.html: ringkasan keunggulan (proof strip) dipindah masuk ke <main>; tombol WhatsApp melayang dibungkus <aside aria-label>
- bmc.html: ditambah <h2> tersembunyi ("Sembilan blok Business Model Canvas") agar urutan heading h1 -> h2 -> h3 benar, tanpa mengubah tampilan
Catatan: axe hanya menangkap sebagian masalah aksesibilitas. Tetap disarankan uji manual dengan keyboard dan pembaca layar (mis. TalkBack/VoiceOver) sebelum peluncuran.

---
# v13
- Foto "Produk unggulan" diganti dengan foto trainer utuh (images/trainer-sistem-starter-lengkap.webp, 900x1600, 134 KB). Foto lama trainer-iot-app.webp dihapus.
- Kotak gambar disesuaikan agar foto tampil utuh (rasio 9:16, lebar maks. 440 px), bukan dipotong 420 px seperti sebelumnya.
- Alt text diperbarui; JSON-LD Product kini memakai foto baru.
- Tabel spesifikasi diperbarui sesuai label pada foto: 8 blok (step down, relay starter, kunci kontak, relay optocoupler, fuse 2 in 2 out, baterai 12V 45Ah, motor starter konvensional, mikrokontroler IoT) + baris Rangka (meja besi hitam beroda).
- styles.css?v=13 (naikkan lagi jika CSS diubah).
Catatan: foto hero kecil ("Trainer asli") masih memakai trainer-iot-panel.webp; belum diganti.

---
# v14
## Keputusan yang diterapkan
1. Isi paket: baterai dan kabel TERMASUK; tablet TIDAK termasuk (aplikasi digunakan lewat tablet milik pembeli).
   Diperbarui di: teks produk, kotak "Isi paket", tabel spesifikasi (baris baru "Termasuk dalam paket"), FAQ (+ pertanyaan "Apakah tablet sudah termasuk?"), meta og:description, JSON-LD Product dan FAQPage.
2. Simulator 3D = bonus khusus pembeli:
   - Tautan publik ke starter.wahyudintamrin.com DIHAPUS dari kedua halaman. Tombol "Buka Simulator Starter" -> "Dapatkan bersama trainer" (#pemesanan); "Coba Simulator" -> "Lihat Demo" (#demo).
   - Kata "gratis dicoba" di halaman Model Bisnis diganti; butir bonus ditandai khusus pembeli.
   - FAQ baru: "Bisakah saya melihat cara kerja trainer sebelum membeli?" (jawaban: skema interaktif + video demo + WhatsApp).
3. Tata letak: kotak "Isi paket" tidak lagi memanjang mengikuti form. styles.css?v=14.
## PENTING (di luar situs ini)
Menghapus tautan hanya menyembunyikan simulator, bukan melindunginya. Siapa pun yang tahu alamat starter.wahyudintamrin.com masih bisa membukanya.
Agar benar-benar khusus pembeli, batasi akses di situs simulator itu sendiri (mis. kode akses/login per pembeli atau password bersama yang diganti berkala).

---
# v15
## Simulator kembali publik
- Tautan https://starter.wahyudintamrin.com/ dipulihkan: tombol "Buka Simulator Starter" (bagian pendamping belajar) dan "Coba Simulator" (bagian kontak).
- Karena publik, simulator TIDAK lagi disebut "bonus/khusus pembeli" (agar tidak menyesatkan). Teks disesuaikan:
  - Bagian "Bonus" -> "Pendamping belajar untuk trainer Anda"; kartu simulator berlabel "Terbuka untuk umum", kartu modul digital berlabel "Bonus pembelian"
  - Kotak "Isi paket" tidak lagi mencantumkan simulator; ditambah kalimat "Simulator 3D dapat dicoba gratis oleh siapa saja"
  - FAQ, tabel spesifikasi, deskripsi og, JSON-LD Product dan FAQPage, halaman Model Bisnis ("simulator gratis dicoba") disamakan
- Modul digital tetap bonus pembeli.
## Foto "Trainer asli" di hero dihapus
- Elemen <figure class="inset"> dihapus, beserta 7 aturan CSS .inset dan file images/trainer-iot-panel.webp (tidak terpakai lagi).
- Ruang kosong di bawah visual hero dihapus (padding-bottom:0).
## Perbaikan bug lama: navigasi overflow di lebar tablet
- Di lebar 621-860 px (ada sejak situs asli v7) menu desktop tidak muat dan tombol tema keluar dari layar.
- Hamburger kini aktif juga untuk 621-900 px (tombol "Hubungi Kami" tampil di dalam menu). Diuji di 31 lebar pada kedua halaman: tidak ada overflow.
