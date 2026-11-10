# **Rapaw: Spek Produk & Panduan Build**

Nov 10, 2026 · @Abiyyu Azmi

## **Ringkasan**

Rapaw adalah rapor pribadi dokter hewan: satu tempat untuk mencatat kegiatan CE, menghitung poin CE dan SKPB, dan melihat ke mana arah belajar bergerak. Tagline: *Your vet report card.*

**Masalah yang diselesaikan**

* Link Log Book Corp Medis tersebar di WhatsApp dan susah dicari.  
* Dokter tidak bisa melihat riwayat unggahan dan total poinnya sendiri.  
* Poin SKPB untuk perpanjangan STRV tercatat terpisah, dan aturan kuota cabang PDHI mudah terlewat.  
* Belum ada gambaran bidang apa yang paling sering dan paling diminati untuk dipelajari, padahal tempat kerja meminta setiap dokter punya *special interest*.

**Pengguna**

* Tahap 1: Abi sendiri (drh., MEDIVET Pet Hospital Bintaro, anggota PDHI PC Banten II).  
* Tahap berikutnya: dokter hewan lain di Indonesia, lalu lebih luas.

**Tujuan**

* Jangka pendek: alat pribadi yang benar-benar dipakai rutin minimal satu bulan.  
* Jangka panjang: produk yang bisa dipakai banyak dokter hewan, dengan rubrik poin per institusi.  
* Sampingan: proses pembuatannya dibagikan sebagai konten *build in public* di Threads (lalu X, mungkin Instagram).

**Prinsip produk**

* Satu kali input. Data dicatat di Rapaw, lalu dikirim ke Log Book Corp tanpa mengetik ulang.  
* Tidak ada angka yang dikunci di kode. Rubrik, target, dan aturan SKPB bisa diedit.  
* Angka di Rapaw adalah **estimasi**. Angka resmi tetap milik Corp Medis dan PDHI.

## **Scope MVP**

MVP berisi sembilan fitur yang sudah disepakati pada 10 November 2026\. Fitur lain menunggu sampai MVP dipakai rutin.

| \# | Fitur | Inti yang harus jalan |
| :---- | :---- | :---- |
| 1 | Login | Hanya pemilik akun yang bisa melihat datanya |
| 2 | Input kegiatan CE | Semua kolom dan kategori di bagian Data per kegiatan |
| 3 | Penerapan ilmu | Skor minat, takeaway, status dan catatan penerapan |
| 4 | Estimasi poin CE | Dihitung dari rubrik MEDIVET yang bisa diedit dan berversi |
| 5 | Pencatatan SKPB | Progress total dan kuota PC Banten II, pengingat perpanjangan |
| 6 | Sertifikat dan lampiran | Sertifikat wajib, lampiran pendukung opsional |
| 7 | Kirim ke Log Book Corp | Tombol yang membuka form Corp dengan isian terisi |
| 8 | Peta pengetahuan sederhana | Heatmap disiplin x spesies, plus disclaimer |
| 9 | Bisa dipasang di HP | PWA, ikon di layar utama |

**Di luar MVP (nanti)**

* Data layanan yang "menghasilkan" di MEDIVET untuk melengkapi peta pengetahuan.  
* Pengingat penerapan 30 hari setelah kegiatan.  
* Multi-user dan rubrik per institusi untuk pengguna lain.  
* Verifikasi otomatis lewat email salinan respons Log Book.  
* Bahasa Inggris (struktur teks sudah disiapkan sejak MVP).

## **Data per kegiatan**

Setiap kegiatan CE adalah satu catatan dengan kolom di bawah. Kolom bertanda wajib harus diisi sebelum disimpan, sisanya boleh menyusul.

**Identitas kegiatan**

| Kolom | Isi | Wajib |
| :---- | :---- | :---- |
| Judul kegiatan | Teks | Ya |
| Penyelenggara | Teks, contoh: PDHI PC Banten II, IPB Training | Ya |
| Tipe penyelenggara | Asosiasi profesi, universitas, industri/sponsor, internal, lainnya | Ya |
| Tanggal mulai dan selesai | Tanggal | Ya |
| Format | Lihat tabel Format di bawah | Ya |
| Peran | Partisipan, narasumber/pemateri, moderator, instruktur hands-on, presenter kasus/poster, panitia, penulis | Ya |
| Mode | Online, offline, hybrid | Ya |
| Lokasi | Dalam negeri, luar negeri | Ya |
| Durasi | Jumlah hari atau sesi, half day/full day, jumlah jam | Ya |
| Level | Basic, intermediate, advanced | Tidak |
| Biaya | Nominal dan siapa yang bayar (pribadi, kantor, sponsor, gratis) | Tidak |
| Topik | Disiplin, spesies, sistem organ (lihat Taksonomi topik) | Disiplin dan spesies wajib |

**Format kegiatan dan pemetaan default ke rubrik MEDIVET**

| Format | Kategori rubrik default |
| :---- | :---- |
| Seminar (offline) | Kursus seminar (DN/LN mengikuti lokasi) |
| Webinar | Webinar |
| Seminar \+ workshop | Kursus workshop |
| Workshop / wetlab offline | Kursus workshop |
| Konferensi / kongres | Kursus seminar, per hari |
| Distance learning / kursus online mandiri | Dipilih manual |
| Weekly course / seri kuliah | Dipilih manual |
| Program sertifikasi | Dipilih manual |
| Magang / externship | Magang (DN/LN mengikuti lokasi) |
| Internal training | Internal Training |
| Journal club / case round | Tidak dihitung (0 poin) |
| Publikasi / poster / artikel | Tidak dihitung (0 poin) |

Peran **narasumber/pemateri** pada kegiatan dalam negeri memakai kategori "Menjadi pembicara", apa pun formatnya. Pemetaan ini bisa diedit, dan pengguna selalu bisa mengganti kategori per kegiatan.

**Penerapan ilmu**

| Kolom | Isi |
| :---- | :---- |
| Skor minat | 1-5, "seberapa ingin saya mendalami topik ini" |
| Takeaway | 1-3 poin yang paling diingat |
| Status penerapan | Belum, sedang dicoba, sudah rutin |
| Catatan penerapan | Teks bebas, contoh: dipakai di kasus kelinci anoreksia, 12 Nov |

**Status pengiriman**

* Status kirim ke Log Book Corp: belum dikirim, sudah dikirim (tanggal).  
* Status poin dari Corp (opsional): belum dicek, sesuai, berbeda (dengan catatan).

## **Taksonomi topik**

Setiap kegiatan diberi tag pada tiga sumbu: disiplin (wajib, boleh lebih dari satu), spesies (wajib, boleh lebih dari satu), dan sistem organ (opsional). Ketiga daftar disimpan sebagai data yang bisa diedit, bukan di kode.

**Sumbu 1: Disiplin**

Acuannya pembagian bidang spesialis AVMA (AS) dan EBVS (Eropa). Kategori yang sebenarnya spesies (misalnya reptil dan amfibi) dipindah ke sumbu spesies.

| Kelompok | Disiplin |
| :---- | :---- |
| Medis | Penyakit Dalam; Kardiologi; Neurologi; Onkologi; Nefrologi & Urologi; Nutrisi Klinis; Dermatologi; Penyakit Infeksius & Mikrobiologi |
| Bedah & prosedur | Bedah Jaringan Lunak; Bedah Ortopedi; Kedokteran Gigi & Bedah Mulut; Oftalmologi |
| Perioperatif & akut | Anestesi & Analgesia; Emergency & Critical Care |
| Diagnostik | Diagnostic Imaging; Patologi Klinik & Laboratorium; Patologi Anatomi |
| Terapi & farmasi | Farmakologi Klinis; Toksikologi; Rehabilitasi & Kedokteran Olahraga |
| Perilaku & kesejahteraan | Perilaku; Kesejahteraan Hewan |
| Reproduksi | Theriogenologi / Reproduksi |
| Populasi & spesies khusus | Kedokteran Zoologi & Eksotik; Shelter Medicine; Hewan Laboratorium; Kesehatan Populasi Hewan Produksi; Kedokteran Preventif, Epidemiologi & Kesmavet |
| Praktik umum | Primary Care / Praktik Umum |
| Non-klinis | Manajemen Praktik & Bisnis; Komunikasi Klien & Tim; Etika, Hukum & Regulasi Veteriner; Pendidikan & Metodologi Riset; Teknologi & AI di Veteriner |

**Sumbu 2: Spesies**

Anjing; kucing; kelinci; rodensia (hamster, guinea pig, chinchilla); mamalia kecil lain (ferret, sugar glider, landak mini); burung peliharaan; unggas; reptil (kura-kura, kadal, ular); amfibi; ikan; primata; satwa liar & kebun binatang; kuda; ruminansia; babi; hewan laboratorium; lintas spesies.

**Sumbu 3: Sistem organ (opsional)**

Integumen; muskuloskeletal; saraf; mata & adneksa; telinga; kardiovaskular; respirasi; rongga mulut & gigi; gastrointestinal; hepatobilier & pankreas; urinari; reproduksi & kelenjar mammae; endokrin & metabolik; hematologi & imunologi; limfatik; multisistemik.

## **Estimasi poin CE**

Poin CE dihitung otomatis dari rubrik MEDIVET-PDHB versi pertama, dengan target 25 poin per semester (Jan \- Jun dan Jul \- Des). Rubrik ini dokumen internal perusahaan: jangan ditampilkan di konten publik, pakai rubrik contoh untuk demo.

**Rubrik versi 1 (berlaku mulai Jul 2026\)**

| Kategori | Satuan | Poin | Varian |
| :---- | :---- | :---- | :---- |
| Kursus dalam negeri, seminar | 1 hari | 3 |  |
| Kursus dalam negeri, workshop | 1 hari | 4 |  |
| Kursus luar negeri, seminar | 1 hari | 4 |  |
| Kursus luar negeri, workshop | 1 hari | 5 |  |
| Menjadi pembicara/pemateri kursus dalam negeri | 1 hari | 3 \- 5 | Half day 3, full day 5 |
| Magang dalam negeri | 1 hari | 3 |  |
| Magang luar negeri | 1 hari | 4 |  |
| Webinar (dalam & luar negeri) | 1 sesi | 1 |  |
| Internal Training | 1 sesi | 2 \- 3 | Half day 2, full day 3 |

**Aturan hitung**

1. Poin kegiatan \= poin per satuan x jumlah satuan (hari atau sesi).  
2. Kategori dengan varian memakai poin half day atau full day sesuai isian durasi.  
3. Kegiatan yang kategorinya "tidak dihitung" bernilai 0, tetapi tetap tampil di riwayat dan peta pengetahuan.  
4. Pengguna boleh menimpa poin per kegiatan (misalnya mengikuti keputusan Corp), dan Rapaw menyimpan nilai asli hasil hitung di samping nilai yang ditimpa.

**Rubrik bisa diedit dan berversi**

* Setiap versi rubrik punya tanggal mulai berlaku.  
* Kegiatan selalu dihitung dengan versi yang berlaku pada tanggal kegiatannya. Jadi mengedit rubrik semester depan tidak mengubah poin kegiatan lama.  
* Mengedit rubrik membuat versi baru. Versi lama tidak dihapus.

**Tampilan**

* Progress semester berjalan: poin saat ini, target 25, sisa hari, dan status (tercapai, sesuai jadwal, tertinggal).  
* Riwayat per semester.

Asumsi yang perlu dikonfirmasi ke Corp Medis: poin kursus multi-hari benar-benar dikalikan jumlah hari.

## **SKPB**

SKPB dihitung per siklus STRV 18 Sep 2024 \- 18 Sep 2029, dengan target minimal 20 (target pribadi 30\) dan minimal 10 dari kegiatan PC Banten II. Hanya kegiatan yang terjadi di dalam rentang berlaku STRV yang dihitung, bukan per tahun kalender.

**Pengaturan (semua bisa diedit)**

| Pengaturan | Nilai awal |
| :---- | :---- |
| Siklus berjalan | 18 Sep 2024 \- 18 Sep 2029 |
| Target minimal | 20 SKPB |
| Target pribadi | 30 SKPB |
| Cabang PDHI | PC Banten II |
| Kuota cabang | Minimal 10 SKPB dari kegiatan yang diselenggarakan PC Banten II |
| Pengingat perpanjangan | 6 bulan sebelum STRV habis (18 Mar 2029\) |

**Kolom SKPB per kegiatan**

| Kolom | Isi |
| :---- | :---- |
| Diakui PDHI? | Ya / tidak. Kegiatan luar negeri otomatis "tidak", bisa diubah |
| Nilai SKPB | Angka, boleh 0 |
| Penyelenggara PDHI | PC Banten II, PC lain (sebutkan), atau bukan PDHI |
| Nomor sertifikat | Teks, opsional |
| Bukti | Sertifikat (wajib bila ada SKPB) dan lampiran pendukung (opsional, bisa lebih dari satu) |

**Aturan**

1. Kegiatan tanpa SKPB tetap tercatat dan tetap dihitung poin CE MEDIVET-nya. Kegiatan itu hanya tidak menambah progress SKPB.  
2. Progress tampil sebagai dua bar: total SKPB terhadap target, dan SKPB dari PC Banten II terhadap kuota 10\.  
3. Status siklus "cukup" hanya bila kedua bar terpenuhi.  
4. Saat siklus baru dimulai, pengguna membuat siklus baru dengan tanggal STRV yang baru. Siklus lama tetap tersimpan.

**Bukti yang disimpan**

Sertifikat adalah bukti utama. Poster atau informasi resmi penyelenggara disimpan sebagai lampiran bila sertifikat tidak mencantumkan nilai SKPB atau tidak jelas menyebut PC penyelenggaranya. Dokumen apa yang diterima saat verifikasi perlu ditanyakan ke PC Banten II.

## **Kirim ke Log Book Corp**

Tombol "Kirim ke Log Book Corp" membuka form Google asli dengan isian yang sudah terisi, lalu pengguna sendiri yang mengunggah sertifikat dan menekan Submit. Rapaw tidak pernah mengirim form secara otomatis, dan cara ini tidak memerlukan akses dari IT atau Corp Medis.

**Alur**

1. Pengguna membuka kegiatan di Rapaw dan menekan tombol kirim.  
2. Rapaw menyusun link pre-filled (parameter entry.\<ID\>=\<nilai\>) dan membukanya di tab baru.  
3. Pengguna mengecek isian, mengunggah sertifikat, menekan Submit di form Google.  
4. Kembali di Rapaw, pengguna menekan "Sudah terkirim". Status dan tanggalnya tersimpan.

**Pemetaan kolom form ke Rapaw**

| Pertanyaan di form | Diisi dari |
| :---- | :---- |
| Nama Dokter | Profil pengguna |
| Cabang | Profil pengguna (MEDIVET Pet Hospital \- Bintaro) |
| Nama Kursus/Pelatihan | Judul kegiatan |
| Institusi/Penyelenggara | Penyelenggara |
| Lokasi Kursus/Pelatihan | Lokasi (Dalam Negeri / Luar Negeri) |
| Tanggal Kursus/Pelatihan | Tanggal mulai |
| Jenis Kursus/Pelatihan | Seminar, Workshop, atau Magang; format lain lewat opsi "Other" berisi nama formatnya |
| Jumlah Hari Kursus/Pelatihan | Durasi dalam hari |
| Sertifikat | Tidak bisa diisi otomatis, diunggah manual |

**Konfigurasi**

* URL form dan ID tiap pertanyaan (entry.xxx) disimpan di pengaturan, bukan di kode.  
* Bila Corp mengubah form, cukup perbarui ID di pengaturan.  
* Langkah pertama build adalah menguji satu link pre-filled di form asli, termasuk opsi "Other" dan format tanggal. Fitur lain dikerjakan setelah uji ini berhasil.

## **Peta pengetahuan**

MVP menampilkan satu heatmap disiplin x spesies, dengan disclaimer yang selalu terlihat di atasnya. Fitur ini dikerjakan paling akhir di MVP.

**Isi tampilan**

* Heatmap: baris \= disiplin, kolom \= spesies, warna sel \= bobot kegiatan.  
* Bobot sel \= jumlah jam kegiatan x faktor level (basic 1, intermediate 1,5, advanced 2). Faktor ini bisa diedit.  
* Dua mode: "Paparan" (peran partisipan) dan "Keahlian" (peran narasumber, instruktur, presenter, penulis).  
* Daftar 5 disiplin dengan rata-rata skor minat tertinggi, di samping 5 disiplin dengan jam terbanyak. Selisih keduanya bahan refleksi.  
* Filter rentang waktu: semester ini, siklus STRV, semua.

**Disclaimer (teks tetap di atas peta)**

*Peta ini menggambarkan kegiatan yang pernah kamu ikuti, bukan bidang yang paling tepat untuk kamu tekuni. Pakai sebagai bahan refleksi, lalu padukan dengan minatmu dan kebutuhan tempat praktikmu.*

**Catatan untuk nanti**

Data mentah peta (jam, level, skor minat per disiplin dan spesies) disimpan rapi supaya kelak bisa dipadukan dengan data layanan yang "menghasilkan" di tempat praktik.

## **Arsitektur dan keamanan**

Rapaw terdiri dari file statis React \+ Vite yang disajikan Cloudflare, dengan semua data di Supabase server Singapura. Di skala pribadi biayanya Rp0, memakai paket gratis ketiga layanan.

![arsitektur Rapaw · 3 layanan, 1 form eksternal][image1]

arsitektur Rapaw · 3 layanan, 1 form eksternal

Aplikasi di HP mengambil file dari Cloudflare, lalu membaca dan menulis data langsung ke Supabase. Form Log Book hanya dibuka, tidak pernah dikirimi data otomatis.

**Aturan keamanan wajib**

1. RLS aktif di setiap tabel sejak tabel dibuat, dan diuji dengan akun kedua.  
2. Kunci service\_role tidak pernah ada di kode aplikasi, repo, atau Cloudflare. Aplikasi hanya memakai kunci publik (anon key).  
3. File .env masuk .gitignore dan tidak pernah di-commit. Repo GitHub privat, dan rubrik asli MEDIVET tidak di-commit (repo hanya memuat rubrik contoh).  
4. Bucket storage sertifikat bersifat privat; hanya pemilik file yang bisa membukanya.  
5. 2FA aktif di GitHub, Supabase, dan Cloudflare. Izin OAuth ke tools pihak ketiga dibatasi seminimal mungkin.  
6. MVP tidak punya kode yang jalan di server (tanpa Next.js), jadi permukaan serangannya kecil.  
7. Ada tombol ekspor data (CSV/JSON) di pengaturan sebagai backup.

**Catatan**

* Proyek Supabase gratis bisa "tidur" bila lama tidak dipakai. Datanya aman, hanya perlu dibangunkan dari dashboard. Cek ketentuan terbarunya saat membuat proyek.  
* Hosting bisa dipindah kapan saja, karena hosting hanya menyimpan file statis tanpa data.

## **Identitas visual**

Rapaw memakai identitas sendiri, terpisah dari MEDIVET, supaya tidak terkesan aplikasi resmi perusahaan. Kesan yang dituju: progres, kredibel, terpercaya, gampang dipakai, tanpa ribet.

**Arah awal (bisa diubah setelah melihat hasilnya)**

| Unsur | Arah | Alasan |
| :---- | :---- | :---- |
| Warna dasar | Hijau-teal tua, sekitar \#0F5C5A | Kesan kesehatan, tenang, dan tepercaya |
| Aksen progres | Kuning kunyit / marigold, sekitar \#F2A93B | Hangat, terasa "pencapaian", kontras dengan teal |
| Netral | Abu-abu hangat dengan sedikit rona teal | Bersih tanpa terasa dingin |
| Status | Hijau (tercapai), kuning (sesuai jadwal), merah (tertinggal) | Dipisah dari warna merek |
| Huruf | Plus Jakarta Sans untuk judul dan isi | Rapi dan mudah dibaca; dirancang foundry Indonesia, jadi ada cerita lokal |
| Angka | Angka tabular (lebar sama) | Poin dan tanggal sejajar rapi di tabel |
| Logo | Jejak kaki yang empat bantalannya terisi bertahap seperti progress | Menggabungkan "paw" dan "rapor" |

**Gaya bahasa**

* Pendek dan ramah, memakai "kamu".  
* Tombol menyebut hasilnya: "Simpan kegiatan", "Kirim ke Log Book".  
* Pesan error menyebut apa yang salah dan cara memperbaikinya.

**Mode gelap**

Tersedia sejak MVP, mengikuti pengaturan HP.

## **Urutan build**

Build dibagi sepuluh tahap kecil, dan setiap tahap selesai bila kriterianya terpenuhi, bukan bila kodenya "sepertinya jalan". Aplikasi sudah online di tahap 5, jadi bisa dicoba di HP lebih awal.

| Tahap | Isi | Selesai bila |
| :---- | :---- | :---- |
| 0 | Persiapan: akun GitHub, Supabase (server Singapura), Cloudflare; install Node.js, Git, Claude Code | Semua akun aktif dengan 2FA, claude bisa dijalankan di terminal |
| 1 | Uji link pre-filled Log Book | Satu link membuka form asli dengan semua kolom terisi benar, termasuk opsi "Other" dan tanggal |
| 2 | Kerangka aplikasi di laptop (React \+ Vite), warna dan huruf dasar | Halaman Rapaw tampil di localhost |
| 3 | Database, login, dan RLS | Login berhasil; akun uji kedua terbukti tidak bisa membaca data akun pertama |
| 4 | Input dan riwayat kegiatan, termasuk penerapan ilmu | Kegiatan bisa ditambah, diubah, dihapus, dan difilter |
| 5 | Online pertama di Cloudflare | Rapaw bisa dibuka dari HP lewat alamat web |
| 6 | Rubrik berversi dan estimasi poin CE | Poin contoh cocok dengan hitungan manual; mengedit rubrik tidak mengubah kegiatan lama |
| 7 | SKPB, sertifikat, dan lampiran | Dua progress bar benar untuk data uji; file tersimpan dan hanya bisa dibuka pemiliknya |
| 8 | Tombol kirim ke Log Book | Kegiatan sungguhan berhasil dikirim lewat tombol, status tersimpan |
| 9 | Peta pengetahuan dan PWA | Heatmap dan disclaimer tampil; Rapaw bisa dipasang di layar utama HP |

**Kebiasaan selama build**

* Satu tahap per sesi Claude Code, lalu commit dan catat di dev log (bahan konten Threads).  
* Setelah tahap 9: pakai Rapaw rutin selama satu bulan sebelum menambah fitur atau mengajak pengguna lain.

## **Panduan sesi pertama**

Sesi pertama punya satu target: menyelesaikan Tahap 0 dan Tahap 1, yaitu semua alat terpasang dan satu link pre-filled terbukti jalan. Analoginya seperti hari pertama di klinik baru: kenalan dengan alat, belum operasi.

**A. Siapkan alat (sekali saja)**

1. **Bikin folder proyek**, misalnya Documents/rapaw. Ini "ruang praktik" Rapaw: semua file ada di sini.  
2. **Install Node.js versi LTS** dari [nodejs.org](https://nodejs.org). Ini "listrik" untuk menjalankan React \+ Vite di laptop.  
3. **Install Git** dari [git-scm.com](https://git-scm.com). Ini "rekam medis" untuk kode: setiap perubahan tercatat dan bisa dibatalkan.  
4. **Install Claude Code.** Ada dua pilihan ([panduan resmi](https://code.claude.com/docs/en/install.md)):  
   * Paling ramah pemula: tab Code di aplikasi desktop Claude, tanpa terminal.  
   * Lewat terminal. Windows (PowerShell): irm https\://claude.ai/install.ps1 \| iex. macOS: curl \-fsSL https\://claude.ai/install.sh \| bash.  
5. **Cek instalasi** di terminal baru: claude \--version lalu claude doctor. Bila claude tidak dikenali, tutup dan buka lagi terminalnya.  
6. **Aktifkan 2FA** di GitHub, Supabase, dan Cloudflare sebelum lanjut.

**B. Siapkan berkas proyek**

1. Simpan file CLAUDE.md ke folder rapaw. Claude Code membacanya otomatis setiap sesi, seperti SOP yang ditempel di dinding ruang praktik.  
2. Ekspor dokumen ini ke Markdown, simpan sebagai rapaw/docs/SPEC.md. Ini "rencana terapi" yang dirujuk CLAUDE.md.

**C. Jalankan sesi**

1. Buka Claude Code di folder rapaw (terminal: masuk ke folder, ketik claude; aplikasi desktop: pilih folder rapaw).  
2. Login dengan akun Claude kamu bila diminta.  
3. Tempel prompt pembuka di bawah.  
4. Setiap kali Claude Code minta izin menjalankan perintah atau mengubah file, baca dulu apa yang diminta. Bila ragu, tanya: "Jelaskan dulu perintah ini buat apa."  
5. Akhiri sesi dengan commit dan satu catatan di docs/DEVLOG.md: apa yang jalan, apa yang bikin bingung.

**Prompt pembuka sesi 1**

Halo\! Aku Abi, dokter hewan dan pemula total di coding. Tolong baca CLAUDE.md dan docs/SPEC.md dulu.

Sesi ini kita kerjakan Tahap 0 dan Tahap 1 saja:  
1\. Cek apakah Node.js dan Git sudah terpasang dengan benar di laptopku, dan inisialisasi git di folder ini.  
2\. Ambil ID setiap pertanyaan (entry.xxx) dari form publik Log Book berikut, lalu simpan di config/logbook-form.json:  
   https\://docs.google.com/forms/d/e/1FAIpQLSf8qNK0s3EPxjuOzEBbLYMiv6KXul42xqmGHhtYQWl4ziLUeg/viewform  
3\. Buat satu link pre-filled berisi kegiatan contoh (format Webinar lewat opsi Other, tanggal hari ini), supaya aku bisa membukanya dan mengecek semua kolom terisi benar. Jangan submit form apa pun.

Aturan: jelaskan setiap langkah dengan bahasa sederhana dan analogi klinik, kerjakan satu langkah per giliran, dan tunggu konfirmasiku sebelum lanjut.  
**Tanda sesi 1 berhasil**

* claude \--version menampilkan nomor versi.  
* Folder rapaw punya CLAUDE.md, docs/SPEC.md, config/logbook-form.json, dan sudah jadi repo git.  
* Link pre-filled membuka form Log Book dengan semua kolom (kecuali sertifikat) terisi benar.

## **Kamus istilah**

Istilah yang akan sering muncul di Claude Code, dengan analogi dunia klinik.

| Istilah | Artinya | Analogi |
| :---- | :---- | :---- |
| Repository (repo) | Folder proyek yang semua perubahannya tercatat | Rekam medis pasien lengkap dengan riwayat kunjungan |
| Git / commit | Menyimpan "foto" kondisi kode pada satu titik | Satu entri SOAP di rekam medis |
| GitHub | Tempat menyimpan repo secara online | Server rekam medis terpusat, aman walau laptop rusak |
| Terminal | Jendela untuk mengetik perintah ke komputer | Interkom langsung ke bagian teknis |
| Node.js / npm | Mesin yang menjalankan kode JavaScript, dan "apotek" paket kodenya | Listrik ruang praktik, dan depo obat |
| Build | Mengubah kode jadi file siap pakai | Meracik bahan baku jadi puyer siap minum |
| Deploy | Menaruh hasil build di hosting supaya bisa diakses | Menaruh obat jadi di etalase apotek |
| Localhost | Aplikasi jalan di laptop sendiri, belum online | Latihan bedah di model |
| Production | Versi yang dipakai sungguhan | Operasi pada pasien |
| Frontend / backend | Bagian yang dilihat pengguna / bagian di belakang layar | Ruang periksa / lab dan gudang |
| Database | Tempat data tersimpan rapi | Lemari rekam medis |
| Storage | Tempat file seperti sertifikat | Gudang arsip |
| Auth | Sistem login | Kartu akses karyawan |
| API | Jalur resmi antar-sistem untuk meminta dan mengirim data | Formulir permintaan lab |
| API key | Kode izin untuk memakai API | Kartu identitas yang ditunjukkan ke petugas lab |
| Environment variable (.env) | Tempat menyimpan kunci dan pengaturan di luar kode | Kunci di laci terkunci, bukan ditempel di pintu |
| RLS | Aturan siapa boleh membaca atau mengubah tiap baris data | Map rekam medis yang dikunci per pemilik |
| Migration | Perubahan struktur database yang tercatat | Revisi format rekam medis yang ada notulensinya |
| PWA | Website yang bisa dipasang seperti aplikasi | Shortcut di layar utama yang rasanya seperti aplikasi asli |
| Bug | Kesalahan pada kode | Efek samping yang tidak terduga |

[image1]: <data:image/png;base64,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>