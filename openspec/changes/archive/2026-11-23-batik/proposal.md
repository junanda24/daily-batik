# Proposal — BATIK! Studio Motif Batik Nusantara

## Apa & kenapa

**BATIK!** adalah web app interaktif tentang motif batik Nusantara: galeri 10 motif
paling ikonik (dengan makna & cerita yang terverifikasi), **Studio** untuk meracik
warna motif sendiri lalu melihatnya di mockup kain & kemeja dan mengunduhnya sebagai
PNG, dan **Kuis Tebak Motif** (kenali motif dari bentuknya, bukan warnanya).

Masalah yang diselesaikan: kebanyakan orang Indonesia memakai batik tanpa tahu
motif yang dipakainya berarti apa. Batik adalah Warisan Budaya Takbenda UNESCO
(2009) dan Hari Batik Nasional tiap 2 Oktober — tapi pengetahuannya tersebar di
artikel panjang yang membosankan. BATIK! mengubahnya jadi sesuatu yang bisa
**dimainkan**: lihat motifnya, utak-atik warnanya, tebak namanya.

## Kenapa ini mengejutkan (efek kejut)

- Bukan katalog foto: **semua motif digambar ulang sebagai pola SVG prosedural
  orisinal** dari struktur geometri aslinya (Kawung = 4 kelopak aren bersilangan,
  Parang = diagonal S tak putus, Mega Mendung = awan berlapis). Polanya hidup —
  bisa diwarnai ulang sesuka hati.
- Twist Studio: pilih motif + palet warna → motif langsung "dibuatkan kainnya"
  di mockup, lalu **unduh PNG pola hasil racikanmu sendiri**. Orang tidak menyangka
  sebuah web batik bisa jadi alat desain mini.
- Twist Kuis: motif ditampilkan dalam palet warna acak — pemain harus mengenali
  dari **bentuk**, bukan warna. Itu cara belajar yang benar-benar nempel.
- Detail batiknya nyata dan terverifikasi (riset web 2026-11-23): Truntum diciptakan
  Permaisuri Sunan Pakubuwana III, Parang Barong dulu hanya untuk raja, merah
  Lasem disebut "merah getih pitik" (merah darah ayam).

## Bentuk output: web app statis (frontend-only, tanpa backend)

Dipilih karena: semua data statis (10 motif + 6 palet + 10 soal kuis), state
pribadi (favorit, skor terbaik) cukup di localStorage, dan hasilnya harus bisa
dibuka siapa pun lewat link publik. Backend tidak menambah apa-apa — dilarang
pakai backend cuma biar kelihatan canggih.

## Uji bar scope

- Bukan utilitas satu fungsi: 3 fitur besar yang saling nyambung (Galeri ↔ Studio
  ↔ Kuis), state bertahan (favorit + skor), alur end-to-end (jelajah → racik →
  unduh → main kuis).
- Bukan sekelas kata-angka/Berani Resign: ada data budaya nyata + alat desain
  interaktif + game. Lolos.

## Skill yang dipakai (ledger jujur)

- `openspec-web-builder` — protokol explore → propose → apply → verify → archive;
  arsitektur & standar kode diikuti (lihat design.md).
- `local-impeccable` — arah desain + craft floor (kontras, spacing, motion,
  anti-default). Mode: Experience/Operate.
- `local-ui-ux-pro-max-skill` — dibaca; isinya hanya catatan pemulihan (recovered
  notes) tanpa panduan operasional, jadi tidak ada aturan tambahan yang diambil
  darinya.
- `local-refero-skill` — riset-dulu & reference lock: arah visual dikunci dari
  material batik itu sendiri (indigo/nila, sogan, merah Lasem, kain mori) +
  riset fakta motif via web; bukan dari template generik.
- Diskip: skill game (bukan game murni), skill backend (tanpa backend),
  skill npm/Flutter (bukan package), skill belanja/pesan/dll (tidak relevan).

## IP check

Semua visual adalah pola SVG orisinal yang digambar dari kode, terinspirasi
struktur geometri motif tradisional — bukan foto/scan kain orang lain, bukan
karakter berlisensi. Fakta motif diverifikasi dari sumber web (jawaku.com,
indonesia.travel, Wikipedia Batik Lasem, blog.knitto.co.id) dan ditulis ulang
dengan kata sendiri. Di footer app dicantumkan catatan bahwa pola adalah
interpretasi digital, bukan foto kain asli.

## Anti-AI-slop

Copy Bahasa Indonesia natural, spesifik, tanpa klise ("jelajahi keindahan",
"warisan yang memukau" dilarang). Setiap motif punya cerita konkret (nama orang,
tempat, aturan keraton) — bukan pujian kosong.
