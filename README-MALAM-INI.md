# Panduan malam ini (Antigravity)

Tujuan: sampai pagi, situs baru sudah dibangun, 14 halaman peluncuran sudah ditulis dan lolos QC, siap kamu tinjau lalu ajukan ke AdSense. Pengajuan JANGAN malam ini.

## 0. Persiapan (30 sampai 45 menit)
1. Buat repo GitHub `heavenka` (private tidak masalah). Salin seluruh isi paket ini ke repo, commit, push ke `main`.
2. Pasang Node 20+ dan buka folder repo di Antigravity.
3. Salin source situs notulen-kita ke `legacy/notulen-kita/`.
4. Cloudflare Pages: buat proyek baru dari repo ini. JANGAN arahkan domain heavenka.app dulu (nanti setelah build lolos dan kamu setuju).
5. Tinjau draf bio di content/site/author-falih.md: hapus semua tanda [CONFIRM ...] dan pastikan setiap kalimat benar. Ko-fi, nama penulis, dan email sudah diisi di docs/brief.md.
6. Hapus subdomain quiz.heavenka.app: hapus record DNS-nya dan proyek Pages-nya di Cloudflare, lalu cek di Search Console bahwa tidak ada halaman quiz yang terindeks.
7. Buat satu worktree git per agent (folder terpisah, cabang terpisah) supaya agent tidak saling menimpa file. Di terminal, dari folder repo:
   ```
   git add . && git commit -m "paket awal" && git branch -M main && git push -u origin main
   git worktree add ../heavenka-desain -b agent/desain
   git worktree add ../heavenka-konten -b agent/konten
   git worktree add ../heavenka-dev -b agent/dev
   ```
   Hasilnya tiga folder: `heavenka-desain`, `heavenka-konten`, `heavenka-dev`. Tiap folder dibuka sebagai workspace terpisah di Antigravity.

## 1. Jalankan dua agent paralel (Agent Manager)
Di Antigravity 2.0: buka Agent Manager, tambahkan workspace `heavenka-desain` dan `heavenka-konten`, mulai percakapan baru di masing-masing, lalu tempel prompt berikut. Sebelum agent mengeksekusi, baca dulu rencananya (artifact plan) dan setujui hanya bila sesuai file perannya. Atur izin supaya perintah terminal dan akses di luar folder proyek meminta persetujuanmu.
Alternatif: folder `.agents/agents/` memuat pembungkus tipis untuk tiap peran (konten, desainer, developer, adsense-guide, sosial, qc). Bila Antigravity mendeteksinya, kamu bisa memilihnya lewat panel /agents. Bila tidak muncul, abaikan dan pakai prompt di bawah; hasilnya sama karena aturan sebenarnya ada di AGENTS.md dan agents/.

**Agent Desainer (cabang agent/desain):**
> Baca AGENTS.md, lalu agents/02-desainer.md, lalu docs/design-brief.md dan docs/brief.md. Kerjakan semua output di file peranmu di cabang agent/desain. Berhenti setelah selesai dan tulis ringkasan 5 baris untukku. Jangan menyentuh folder content/.

**Agent Konten (cabang agent/konten):**
> Baca AGENTS.md, lalu agents/01-konten.md, docs/content-standards.md, docs/launch-set.md. Tulis dua halaman pertama saja: meeting-minutes (induk) dan meeting-minutes/board-of-directors (anak), lengkap dengan cek SERP dan unique_angle. Jalankan node scripts/qc/run.mjs. Lalu BERHENTI dan minta aku meninjau sebelum lanjut.

## 2. Gerbang tinjauan pertamamu (jangan lewati)
- Baca dua halaman Konten dengan mata pembaca di HP. Tanya dirimu: apakah ini lebih berguna daripada 5 hasil teratas Google? Jika tidak, kembalikan dengan catatan spesifik. Mutu dua halaman ini menentukan 12 halaman sisanya.
- Lihat design/components.html dan page-mockup.html di browser (375px dan lebar penuh). Periksa daftar "Dilarang" di design-brief.
- Setelah setuju, catat di docs/decisions.md (G1 untuk desain).

## 3. Lanjutkan
**Agent Developer (cabang agent/dev), setelah G1:**
> Baca AGENTS.md, agents/03-developer.md, docs/design-brief.md, dan folder design/. Bangun situs sesuai spesifikasi, commit kecil, jalankan npm run build dan node scripts/qc/run.mjs setelah tiap tahap. Jangan mengubah isi content/.

**Agent Konten, lanjutan:**
> Lanjutkan halaman sisa di launch-set.md berurutan (urutan nomor). Satu pilar per PR. Setelah tiap pilar, jalankan QC dan perbaiki semua BLOCKER dan MAJOR. Berhenti di pilar berikutnya bila ada halaman yang unique_angle-nya tidak bisa kamu pertanggungjawabkan.

Halaman situs (about, contact, privacy, terms, editorial-policy) ditulis Konten di akhir. Bio penulis sudah ada drafnya (author-falih.md); agent dilarang mengubahnya.

## 4. QC dan pra-submit (pagi hari)
Buka sesi baru (konteks baru) untuk setiap agent berikut.
> Baca AGENTS.md dan agents/06-qc.md. Audit repo dan situs sesuai file peranmu, tulis qc/report-YYYYMMDD.md.

> Baca AGENTS.md, agents/04-adsense-guide.md, docs/adsense-playbook.md. Jalankan mode B (audit pra-submit). Ambil kebijakan resmi Google saat ini sebelum memberi verdict.

Gerbang pra-submit otomatis: di GitHub, Actions → QC → Run workflow → presubmit = true.

## 5. Sebelum ajukan
- Gabungkan cabang ke main setelah kamu tinjau, lalu arahkan DNS heavenka.app ke proyek Pages baru.
- Pastikan bio penulis sudah ditulis dan halaman author berstatus published.
- Ajukan ke AdSense hanya bila AdSense Guide menyatakan SIAP dan QC tanpa BLOCKER/MAJOR.

## Yang TIDAK dijalankan malam ini
Agent Sosial (05-sosial.md). Mulai setelah minimal 5 halaman terbit.

## Jika waktu mepet
- Prioritas 1: desain + build + 2 halaman contoh yang bagus.
- Prioritas 2: pilar meeting-minutes lengkap (6 halaman) + halaman situs.
- Prioritas 3: resignation, incident, employment verification.
Lebih baik 8 halaman bagus daripada 14 yang tergesa. Pengajuan boleh ditunda sampai set lengkap.

## Jika agent macet atau menyimpang
Hentikan, buka AGENTS.md, dan tulis ulang instruksinya lebih sempit. Jangan biarkan agent mengerjakan hal di luar file perannya.
