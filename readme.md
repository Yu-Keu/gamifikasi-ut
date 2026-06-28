# SQ3R UT Quest Buddy — Edisi RPG Akademis

**SQ3R UT Quest Buddy** adalah aplikasi asisten belajar mandiri berbasis web (_single-page application_) yang dirancang khusus untuk mahasiswa Universitas Terbuka (UT). Aplikasi ini menggabungkan metode belajar terstruktur **SQ3R** (_Survey, Question, Read, Recite, Review_) dengan elemen gamifikasi **RPG** (_Role-Playing Game_) retro untuk membantu meningkatkan ketahanan belajar mandiri dan melawan prokrastinasi.

Aplikasi ini bersifat serverless, berjalan sepenuhnya di sisi klien (_client-side_), dan memanfaatkan integrasi API LLM (seperti Google Gemini, OpenAI, atau OpenRouter) untuk memberikan analisis materi, evaluasi pemahaman, serta kuis HOTS secara dinamis.

---

## Akses Website

Laman aplikasi: [SQ3R](https://yu-keu.github.io/gamifikasi-ut/)

Laman arsip pelajaran: [Portal Belajar Mandiri UT](https://yhuzued.github.io/sistem-belajar-ut/) (khusus milik saya, Yusuf, sebagai pemilik dan pengguna website)

---

## 🎮 Fitur Utama

### 1. Metodologi SQ3R Terintegrasi AI

- **S - Survey:** AI menganalisis draf atau modul BMP (_Buku Materi Pokok_) Anda untuk merumuskan gambaran umum peta kognitif materi.
- **Q - Question:** Mengubah poin-poin penting survei menjadi pertanyaan-pertanyaan pemandu belajar kritis secara otomatis dalam format JSON.
- **R1 - Read (Active Reading):** Aktivitas membaca mandiri yang dibantu oleh _Timer Pomodoro_ interaktif dan fitur coretan catatan.
- **R2 - Recite:** Anda menuliskan jawaban dari ingatan kognitif Anda tanpa melihat buku, yang kemudian dievaluasi secara konstruktif oleh Tutor AI dengan tambahan analogi dunia nyata.
- **R3 - Review:** AI menyusun kuis interaktif standar _Higher Order Thinking Skills_ (HOTS) berisi 3 pilihan ganda untuk menguji pemahaman akhir Anda.

### 2. Gamifikasi RPG Akademis

- **Kelas Karakter:** Anda dapat memilih salah satu dari tiga guild dengan bonus pasif eksklusif:
  - **Kesatria Pomodoro (Warrior):** +20% XP saat fokus membaca (R1).
  - **Penyihir Kritis (Mage):** +20% XP pada tahap survei dan tanya jawab (S, Q, & R2).
  - **Pencuri Skor (Rogue):** +20% XP pada pengerjaan kuis cepat (R3).
- **HUD Status RPG:** Memantau level, XP, _Focus Shield_ (HP), akumulasi _Gold_, serta _Daily Streak_ belajar.
- **Pertempuran Prokrastinasi:** Menghadapi "Demon Prokrastinasi" di mana HP bos akan berkurang secara bertahap seiring berjalannya waktu fokus pada timer Pomodoro.
- **Kedai Ramuan Belajar:** Gunakan emas yang Anda dapatkan untuk membeli item pendukung seperti _Ramuan Fokus_ (Pengali XP 1.5x) atau memulihkan stamina fokus kembali ke 100%.
- **Peta Dungeon BMP UT:** Modul ceklis interaktif untuk melacak penyelesaian bab fisik dalam dunia nyata dengan imbalan bonus XP & Gold.

### 3. Fitur Aksesibilitas & Kenyamanan

- **Immersive Focus Reading Mode:** Antarmuka membaca minim gangguan dengan dukungan pengaturan jenis font (Serif/Sans-Serif), ukuran teks, dan tema warna.
- **Multi-Tema:** Dukungan pergantian tema instan (Slate Light, Warm Sepia, dan Night Dark).
- **Ekspor Laporan (.HTML):** Unduh ringkasan hasil belajar, catatan pribadi, jawaban, dan kuis yang telah Anda kerjakan ke dalam satu berkas HTML terpisah untuk referensi belajar offline.

---

## 🛠️ Teknologi yang Digunakan

Aplikasi ini dibangun menggunakan pustaka modern tanpa memerlukan proses kompilasi (_build step_):

- **Tailwind CSS (via CDN):** Desain antarmuka responsif dan modern.
- **Alpine.js (via CDN):** Manajemen state aplikasi yang ringan dan reaktif.
- **Marked.js & KaTeX:** Rendering sintaksis Markdown serta formula matematika secara real-time.
- **Local Storage API:** Menyimpan data sesi belajar, preferensi tema, status RPG, dan API Key secara aman di dalam peramban lokal Anda.

---

## 🚀 Cara Menjalankan

Aplikasi ini tidak memerlukan instalasi server lokal.

1. Unduh berkas `index.html` (atau salin seluruh kode HTML yang tersedia).
2. Klik dua kali pada file tersebut untuk membukanya langsung menggunakan peramban web modern apa pun (Google Chrome, Mozilla Firefox, Microsoft Edge, Safari, dll.).
3. Anda juga dapat meng-host file ini di platform gratis seperti GitHub Pages, Netlify, atau Vercel.

---

## ⚙️ Konfigurasi API

Untuk mengaktifkan asisten AI, Anda memerlukan API Key yang valid:

1. Buka aplikasi, lalu klik tombol **API** pada sudut kanan atas (atau klik tombol tautan di banner peringatan).
2. Pilih penyedia layanan yang ingin digunakan:
   - **Google Gemini API** (Direkomendasikan. Model default: `gemini-3.5-flash`).
   - **OpenRouter API** (Dapat menghubungkan berbagai model open-source).
   - **OpenAI API** (Model default: `gpt-4o-mini` atau model kompatibel lainnya).
3. Masukkan API Key Anda pada kolom yang disediakan.
4. Klik tombol **Tes Konektivitas Jalur API Utama** untuk menguji konfigurasi Anda sebelum mulai belajar.

_Catatan: API Key Anda disimpan langsung di browser menggunakan `localStorage` dan tidak pernah dikirim ke server pihak ketiga mana pun selain ke penyedia layanan API yang Anda pilih secara langsung._

---

## 📂 Struktur Penyimpanan Data (Local Storage)

Aplikasi ini mengelola data pada perangkat lokal melalui kunci penyimpanan berikut:

- `ut_sq3r_settings_v8_rpg`: Menyimpan preferensi provider API, model yang digunakan, dan API Key Anda.
- `ut_sq3r_session_v8_rpg`: Menyimpan progres belajar aktif, catatan, daftar pertanyaan, kuis, dan data status RPG (Level, Gold, HP, dsb).
- `ut_sq3r_theme_v8_rpg`: Menyimpan preferensi tema warna yang aktif.
- `ut_sq3r_font_v8_rpg`: Menyimpan preferensi jenis font pada mode fokus.
- `ut_sq3r_last_study_date`: Digunakan untuk memvalidasi pemeliharaan _streak_ belajar harian.
