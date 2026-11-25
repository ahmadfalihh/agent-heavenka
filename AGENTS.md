# AGENTS.md — Proyek heavenka.app

## Misi
Mengganti seluruh isi heavenka.app dengan situs template dokumen kerja berbahasa Inggris (US) untuk pasar Amerika Serikat: meeting minutes, resignation letter, incident report, employment verification. Tujuan utama: lolos Google AdSense (bukan ditolak karena thin / low value content), lalu tumbuh lewat pencarian organik. Konten Indonesia (generator notulen lama) hidup di /id/.

## Pemilik dan bahasa
- Pemilik: Ahmad Falih Hadika (dipanggil Falih). Fakta tetap (byline, email, Ko-fi) ada di docs/brief.md. Bicara kepada Falih dalam Bahasa Indonesia, singkat, tanpa basa-basi.
- Semua isi situs di luar /id/: English (US). Isi /id/: Bahasa Indonesia.
- Dokumen proyek (file ini, agents/, docs/): Bahasa Indonesia.

## Aturan mutlak
1. Jangan mengarang: data, statistik, pasal hukum, kutipan, testimoni, ulasan, kredensial penulis. Tidak yakin: tulis "perlu verifikasi" di deskripsi PR, jangan di halaman.
2. Jangan menyalin teks dari situs lain (Template.net, Indeed, Canva, dll). Semua teks template dan penjelasan ditulis orisinal.
3. Satu agent = satu cabang git: `agent/desain`, `agent/dev`, `agent/konten`, `agent/qc`, `agent/sosial`. Dilarang push langsung ke `main`.
4. Jangan menyentuh kredensial, file .env, DNS, pengaturan Cloudflare, atau akun Google/AdSense. Itu tugas Falih.
5. Kualitas di atas jumlah. 10 halaman yang lolos kontrak lebih baik daripada 40 yang tipis.
6. Setiap klaim tentang kebijakan AdSense/Google harus berasal dari halaman resmi Google yang diambil pada saat itu, bukan dari ingatan.
7. Jangan menerbitkan apa pun ke media sosial. Hanya menyiapkan draf.
8. Jangan memasang kode iklan AdSense sebelum Falih menyetujui. Slot iklan dirancang tapi nonaktif.
9. Data pribadi Falih TIDAK BOLEH masuk repo, konten, atau situs: NIP, NIK/KTP, nomor HP, alamat rumah, tanggal lahir, data keluarga, email pribadi, agama, status perkawinan. Satu-satunya kontak publik adalah email di docs/brief.md. Jika menemukan data semacam itu di repo, hapus dan laporkan.

## Baca sebelum bekerja
docs/brief.md, docs/launch-set.md, docs/keyword-map.csv, docs/content-standards.md, docs/design-brief.md, docs/adsense-playbook.md, docs/decisions.md, docs/rejection-log.md, lalu file peranmu di agents/.

## Alur gerbang
G1 Desain (token + komponen disetujui Falih) → G2 Build (situs berjalan, 2 halaman contoh) → G3 Konten (tiap halaman lolos kontrak) → G4 QC (nol BLOCKER dan MAJOR) → G5 Pra-submit AdSense (checklist 100%) → Falih menyetujui → ajukan.
Tidak ada agent yang boleh melompati gerbang. Hasil tiap gerbang dicatat di docs/decisions.md (tanggal, peran, hasil).

## Definisi selesai
Bukan "sudah ditulis", melainkan: `node scripts/qc/run.mjs` lolos untuk bagianmu, dan PR berisi (a) apa yang berubah, (b) daftar yang perlu diverifikasi manusia, (c) sumber yang dipakai, (d) hasil QC lokal.

## Eskalasi
Jika instruksi bertentangan atau data tidak ada: berhenti dan tulis pertanyaan untuk Falih di PR. Jangan menebak.
