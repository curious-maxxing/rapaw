# CLAUDE.md: Rapaw

Rapaw adalah rapor pribadi dokter hewan: mencatat kegiatan CE, menghitung estimasi poin CE (rubrik tempat kerja) dan SKPB (perpanjangan STRV, PDHI), mengirim data ke form Log Book kantor lewat link pre-filled, dan menampilkan peta pengetahuan.

Spesifikasi lengkap ada di `docs/SPEC.md`. Itu sumber kebenaran. Kalau CLAUDE.md dan SPEC.md bertentangan, tanyakan ke pengguna, jangan menebak.

---

## 1. Tentang pengguna (baca ini dulu)

- Pengguna: Abi, dokter hewan, **pemula total dalam coding**. Ini proyek pertamanya.
- Bahasa: Bahasa Indonesia yang santai dan natural. Boleh pakai "kamu" atau "lo". Jangan pakai "kau".
- Jangan pakai em dash panjang di teks yang kamu tulis untuk pengguna maupun di UI.
- Setiap konsep teknis baru: jelaskan dengan bahasa sederhana + analogi dunia klinik (contoh: database = lemari rekam medis, commit = satu entri SOAP, RLS = map rekam medis yang dikunci per pemilik, localhost = latihan bedah di model, production = operasi pada pasien).
- Kerjakan **satu langkah per giliran**. Sebelum langkah besar, tunjukkan rencana singkat dan tunggu konfirmasi.
- Sebelum menjalankan perintah terminal, jelaskan dalam satu kalimat perintah itu untuk apa.
- Kalau ada pilihan teknis, beri rekomendasi + alasan singkat, jangan sodorkan lima opsi.
- Di akhir sesi: ringkas apa yang selesai, apa yang belum, dan tambahkan catatan ke `docs/DEVLOG.md`.

## 2. Stack (sudah diputuskan, jangan diganti tanpa izin)

| Bagian | Pilihan |
|---|---|
| Frontend | React + Vite + TypeScript |
| Styling | Tailwind CSS |
| Routing | React Router |
| Backend | Supabase (Auth, Postgres, Storage), region Singapura |
| Hosting | Cloudflare (file statis) |
| PWA | vite-plugin-pwa |
| Tes | Vitest, terutama untuk logika hitung poin |

- **Tidak ada Next.js** dan **tidak ada kode yang jalan di server** pada MVP. Semua logika di frontend + aturan di database (RLS).
- Jangan menambah layanan berbayar atau layanan pihak ketiga baru tanpa izin.
- Sebelum memasang paket npm baru, jelaskan fungsinya dan kenapa perlu.

## 3. Aturan keamanan (tidak bisa ditawar)

1. **RLS aktif di setiap tabel** sejak tabel dibuat. Setiap tabel punya kolom `user_id uuid not null references auth.users`, dan policy select/insert/update/delete: `user_id = auth.uid()`.
2. Setelah membuat tabel/policy, **uji dengan akun kedua** bahwa data akun pertama tidak bisa dibaca.
3. **Kunci `service_role` tidak pernah** ada di kode frontend, di repo, di Cloudflare, atau ditampilkan di chat. Frontend hanya memakai `VITE_SUPABASE_URL` dan `VITE_SUPABASE_ANON_KEY`.
4. `.env` dan `.env.local` wajib ada di `.gitignore`. Sediakan `.env.example` tanpa nilai asli.
5. Bucket storage `certificates` bersifat **privat**. Path file: `<user_id>/<activity_id>/<nama-file>`. Policy storage hanya mengizinkan pemilik folder.
6. Repo GitHub bersifat **privat**.
7. Rubrik poin MEDIVET adalah dokumen internal kantor. **Jangan** taruh nilainya di file yang di-commit. Repo hanya berisi rubrik contoh (`supabase/seed.example.sql`). Rubrik asli dimasukkan lewat halaman Pengaturan atau `supabase/seed.local.sql` (masuk `.gitignore`).
8. Jangan pernah mengirim (submit) form Google secara otomatis. Rapaw hanya membuka link pre-filled; pengguna yang menekan Submit.
9. Semua perubahan skema database lewat file migration di `supabase/migrations/`, bukan klik manual di dashboard.

## 4. Model data (ringkas; detail di SPEC.md)

Semua tabel punya `id`, `user_id`, `created_at`, `updated_at`.

- `profiles`: nama tampilan, cabang tempat kerja (untuk form Log Book), bahasa.
- `activities`: judul, penyelenggara, tipe_penyelenggara, tanggal_mulai, tanggal_selesai, format, peran, mode, lokasi (`DN` | `LN`), durasi_hari, durasi_sesi, varian_hari (`half` | `full` | null), jam, level, biaya, dibayar_oleh, skor_minat (1-5), takeaway, status_penerapan, catatan_penerapan, rubric_item_code (kategori rubrik terpilih), poin_ce_hitung, poin_ce_override (nullable), skpb_diakui (bool), skpb_nilai (numeric, boleh 0), skpb_penyelenggara (`branch` | `other_pc` | `non_pdhi`), skpb_pc_lain, nomor_sertifikat, status_logbook (`belum` | `terkirim`), tanggal_kirim_logbook, status_cek_corp, catatan_cek_corp.
- `taxonomy_items`: axis (`discipline` | `species` | `organ_system`), group_name, name, sort_order, active. Diisi seed default dari SPEC.md, bisa diedit pengguna.
- `activity_topics`: activity_id, taxonomy_item_id (many-to-many).
- `rubric_versions`: name, effective_from (date).
- `rubric_items`: rubric_version_id, code, label, unit (`hari` | `sesi`), points, points_half_day, points_full_day, counts (bool, false = "tidak dihitung").
- `format_mappings`: format, rubric_item_code default, lokasi-aware (bool). Bisa diedit.
- `skpb_cycles`: start_date, end_date, target_min, target_personal, branch_name, branch_quota, reminder_months_before, is_active.
- `attachments`: activity_id, kind (`certificate` | `supporting`), storage_path, file_name.
- `logbook_config`: form_url, entry_ids (jsonb: pemetaan pertanyaan form ke `entry.xxx`), branch_value.
- `settings`: semester target (default 25), faktor level peta (basic 1, intermediate 1.5, advanced 2).

## 5. Aturan bisnis

**Poin CE**
- Poin = poin per satuan x jumlah satuan (hari atau sesi).
- Kategori dengan varian half/full day memakai `points_half_day` / `points_full_day`.
- Versi rubrik yang dipakai = versi dengan `effective_from` terbaru yang <= tanggal_mulai kegiatan. Mengedit rubrik membuat versi baru; versi lama tidak dihapus dan kegiatan lama tidak berubah.
- Peran narasumber/pemateri + lokasi DN memakai kategori "Menjadi pembicara".
- `poin_ce_override` (kalau diisi) menang untuk tampilan total, tetapi `poin_ce_hitung` tetap disimpan.
- Semester: 1 Jan - 30 Jun dan 1 Jul - 31 Des. Target default 25.
- Status semester: tercapai (>= target), sesuai jadwal (poin/target >= persentase semester berjalan), tertinggal (sisanya).
- Logika hitung ditulis sebagai fungsi murni di `src/lib/points.ts` dengan tes Vitest.

**SKPB**
- Siklus aktif awal: 18 Sep 2024 - 18 Sep 2029, target minimal 20, target pribadi 30, cabang PC Banten II, kuota cabang minimal 10, pengingat 6 bulan sebelum habis.
- Yang dihitung hanya kegiatan dengan `skpb_diakui = true` dan tanggal_mulai di dalam rentang siklus.
- Kegiatan lokasi LN: `skpb_diakui` default `false` (bisa diubah pengguna).
- Kuota cabang dihitung dari kegiatan dengan `skpb_penyelenggara = 'branch'`.
- Status "cukup" hanya bila total >= target_min **dan** kuota cabang terpenuhi.
- Logika di `src/lib/skpb.ts` dengan tes.

**Log Book (link pre-filled)**
- Bangun URL: `<form_url>?usp=pp_url&entry.<id>=<nilai>&...` dengan `encodeURIComponent`.
- Jenis kegiatan: Seminar/Workshop/Magang langsung; format lain lewat `entry.<id>=__other_option__&entry.<id>.other_option_response=<nama format>`.
- Tanggal: format `YYYY-MM-DD` (verifikasi di Tahap 1).
- Sertifikat tidak bisa diisi otomatis.
- Setelah membuka link, tampilkan tombol "Sudah terkirim" untuk mencatat status.

**Peta pengetahuan**
- Heatmap disiplin x spesies. Bobot sel = jam x faktor level.
- Mode "Paparan" (peran partisipan) dan "Keahlian" (narasumber, instruktur, presenter, penulis).
- Disclaimer dari SPEC.md selalu tampil di atas peta.

## 6. UI dan bahasa

- Semua teks UI di file locale (`src/locales/id.json`), bukan ditulis langsung di komponen. Bahasa Inggris menyusul.
- Mobile-first. Mode gelap mengikuti pengaturan HP.
- Identitas: teal tua (~#0F5C5A) sebagai warna dasar, marigold (~#F2A93B) untuk progres, huruf Plus Jakarta Sans, angka tabular. Detail di SPEC.md bagian Identitas visual.
- Tombol menyebut hasilnya ("Simpan kegiatan", "Kirim ke Log Book"). Pesan error menyebut apa yang salah dan cara memperbaikinya.

## 7. Cara kerja per sesi

1. Baca `docs/SPEC.md` bagian Urutan build. Kerjakan **satu tahap per sesi**.
2. Tunjukkan rencana tahap itu dalam 3-6 poin, tunggu "ok".
3. Kerjakan langkah demi langkah, jelaskan dengan analogi.
4. Cek kriteria "Selesai bila" tahap itu bersama pengguna.
5. Commit dengan pesan jelas dalam bahasa Indonesia, misalnya `tahap 3: tabel activities + RLS`.
6. Tambahkan entri ke `docs/DEVLOG.md`: tanggal, tahap, yang selesai, yang membingungkan, pelajaran.

## 8. Struktur folder (target)

```
rapaw/
  CLAUDE.md
  docs/
    SPEC.md
    DEVLOG.md
  config/
    logbook-form.json
  supabase/
    migrations/
    seed.example.sql
    seed.local.sql      (gitignored)
  src/
    lib/        (points.ts, skpb.ts, logbook.ts, supabase.ts)
    locales/    (id.json)
    pages/
    components/
  .env.example
  .gitignore
```
