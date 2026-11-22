# Spec — BATIK! Studio Motif Batik Nusantara

## Data motif (10, terverifikasi 2026-11-23)

| # | Motif | Asal | Kategori | Makna singkat | Cerita (tampil di detail) |
|---|-------|------|----------|---------------|---------------------------|
| 1 | Kawung | Yogyakarta & Solo | Keraton | Kesucian & pengendalian diri | Bentuknya irisan buah aren/kolang-kaling: empat kelopak bersilangan. Melambangkan kesempurnaan, keseimbangan hidup, dan pengendalian diri. Dulu hanya dipakai kalangan keraton; kini dipakai acara resmi & keagamaan. |
| 2 | Parang | Yogyakarta & Solo | Keraton | Kekuatan & keberanian | Garis diagonal bentuk S yang tak pernah putus, seperti ombak. Melambangkan semangat pantang menyerah, keteguhan, dan keberanian. Motif tertua & paling sakral; varian Parang Barong dulu hanya boleh dipakai raja. |
| 3 | Mega Mendung | Cirebon | Pesisir | Kesabaran & keteduhan hati | Awan berlapis khas pesisir Cirebon, hasil akulturasi Jawa–Tionghoa. Awan melambangkan kesabaran dan pikiran yang jernih di tengah badai. Warna cerah: biru, merah, ungu. |
| 4 | Truntum | Solo | Keraton | Cinta yang tumbuh kembali | Diciptakan Permaisuri Sunan Pakubuwana III. "Tumaruntum" = tumbuh kembali. Bintang-bintang kecil yang tersebar. Dipakai orang tua pengantin sebagai doa agar rumah tangga anaknya harmonis dan langgeng. |
| 5 | Sido Mukti | Solo & Yogyakarta | Pernikahan | Makmur & bahagia | "Sido" = jadi/terjadi, "mukti" = makmur/mulia. Harapan pemakainya hidup makmur dan bahagia. Motif wajib di banyak pernikahan adat Jawa. |
| 6 | Sekar Jagad | Yogyakarta & Solo | Keraton | Keindahan & keberagaman dunia | "Sekar" = bunga, "jagad" = dunia; juga dibaca "kar jagad" = peta dunia. Petak-petak tak beraturan seperti pulau-pulau, masing-masing berisi motif kecil. |
| 7 | Buketan | Pekalongan | Pesisir | Keindahan flora pesisir | Buket bunga khas batik pesisir Pekalongan, pengaruh Eropa. Warna-warni cerah, jauh dari kesan keraton yang kalem. |
| 8 | Lasem | Lasem, Rembang | Pesisir | Akulturasi Tionghoa–Jawa | Merah khas "merah getih pitik" (merah darah ayam). Motif naga = harapan mulia & kekuatan; burung hong = keindahan & keabadian. Batik Tiga Negeri: merah = Tionghoa, sogan = Jawa, biru = Belanda. |
| 9 | Sido Asih | Yogyakarta & Surakarta | Pernikahan | Kasih sayang & keharmonisan | "Sido" = jadi, "asih" = kasih sayang. Harapan hidup dipenuhi kasih sayang dan hubungan yang langgeng. Sering dipakai di pernikahan. |
| 10 | Lereng | Jawa | Keraton | Perlindungan & penyertaan | Garis-garis miring geometris yang tersusun teratur. Melambangkan perlindungan dan penyertaan bagi pemakainya. |

## Palet Studio (6)

1. Klasik Sogan — kain krem `#F3EAD8`, motif sogan `#7A4A21`, aksen `#A67C37`
2. Indigo Keraton — kain indigo `#1E3A5F`, motif krem `#F3EAD8`, aksen `#7FA8C9`
3. Lasem Merah — kain merah `#A63A2B`, motif krem `#F7EFE0`, aksen `#E8B04B`
4. Pesisir Cerah — kain biru `#2E7D9E`, motif krem `#FDF6E3`, aksen `#E2725B`
5. Hijau Botol — kain hijau `#1F4D3A`, motif krem `#F3EAD8`, aksen `#C9A227`
6. Monokrom — kain arang `#26221F`, motif krem `#F5EFE2`, aksen `#8C8578`

## Requirements

### R1 — Galeri motif
- SHALL menampilkan 10 kartu motif, tiap kartu: pola SVG motif, nama, asal daerah,
  satu baris makna.
- SHALL menyediakan pencarian teks (nama/asal/makna) dan filter chip:
  Semua / Keraton / Pesisir / Pernikahan.
- WHEN pengguna mengetuk kartu THEN tampil detail (nama, asal, makna, cerita
  lengkap, "dipakai untuk") + tombol "Coba di Studio" yang membuka Studio dengan
  motif itu terpilih.
- WHEN pengguna mengetuk bintang THEN motif masuk/keluar favorit, tersimpan di
  localStorage, dan filter "Favorit" menampilkannya.

### R2 — Pola SVG orisinal
- SHALL menggambar tiap motif sebagai pola SVG prosedural dari struktur
  geometrinya (bukan gambar/foto): Kawung 4 kelopak, Parang diagonal S,
  Mega Mendung awan berlapis, Truntum bintang kecil, Sido Mukti belah ketupat,
  Sekar Jagad petak pulau, Buketan bunga, Lasem sulur+naga-stylized/bunga,
  Sido Asih bunga kecil, Lereng garis miring.
- SHALL mewarnai pola dari parameter palet (kain, motif, aksen) sehingga satu
  fungsi pola bisa dipakai di semua palet.

### R3 — Studio
- SHALL memungkinkan pilih motif (strip tile) + pilih palet (6 swatch) dengan
  preview langsung.
- SHALL menampilkan preview pada mockup kain (persegi besar berpola) dan mockup
  kemeja (siluet kemeja berisi pola).
- SHALL menyediakan tombol "Acak" (kombinasi motif+palet acak) dan "Unduh PNG"
  (ekspor tile pola sebagai file PNG via canvas).
- WHEN motif/palet berubah THEN preview berubah dengan transisi halus (bukan
  lompatan instan).

### R4 — Kuis Tebak Motif
- SHALL menyajikan 10 soal (satu per motif, urutan acak): tampilkan tile pola
  dalam palet acak + 4 pilihan nama motif.
- SHALL memberi umpan balik langsung tiap jawaban (benar/salah + satu kalimat
  penjelasan motif yang benar) dan skor berjalan + progress.
- SHALL menampilkan layar hasil: skor, gelar (10 = "Maestro Batik", 8–9 =
  "Pembatik Mahir", 5–7 = "Pecinta Batik", 3–4 = "Pembatik Pemula", 0–2 =
  "Masih Meraba Kain"), skor terbaik tersimpan di localStorage, tombol "Main Lagi".

### R5 — Navigasi & struktur
- SHALL punya 3 tab: Galeri, Studio, Kuis — bottom nav di HP, top nav di desktop.
- SHALL memakai hash routing (`#galeri`, `#studio`, `#kuis`) agar tab bisa
  dibagikan/di-bookmark.
- SHALL menampilkan hero: judul BATIK!, subjudul satu kalimat, 3 fakta
  (10 motif, UNESCO 2009, Hari Batik 2 Oktober), CTA ke Galeri & Kuis.
- SHALL menampilkan footer dengan catatan pola orisinal + sumber fakta.

### R6 — Kualitas
- SHALL mobile-first, semua kontrol bisa dipakai dengan sentuhan, teks terbaca
  tanpa zoom.
- SHALL tanpa lorem ipsum, tanpa tombol mati, tanpa error console.
- SHALL copy Bahasa Indonesia natural, tanpa klise AI.
