# 🎲 Snake and Ladders Educational Game (EduSnake)

> **EduSnake** — Platform Game Ular Tangga Edukatif Multi-Mata Pelajaran & Multi-Kelas Berbasis Web untuk Pembelajaran Interaktif SMA/MA/SMK.

---

## 📖 About the Project

**EduSnake** adalah platform game Ular Tangga edukatif berbasis web yang menggabungkan alur permainan papan Ular Tangga klasik dengan sistem kuis pendidikan dinamis multi-mata pelajaran, multi-kelas, dan multi-tingkat kesulitan. Game ini dikembangkan dari _base project_ original milik **[Yashksaini](https://github.com/yashksaini)** dan mengalami ekspansi arsitektur besar-besaran untuk mengubahnya dari game berfokus satu pelajaran menjadi platform pembelajaran interaktif yang fleksibel dan terstruktur.

---

## 🎯 Project Objectives

- **Gamifikasi Pembelajaran**: Mengubah proses evaluasi dan kuis materi pelajaran menjadi permainan Ular Tangga yang menyenangkan dan kompetitif.
- **Dukungan Multi-Kelas & Multi-Mapel**: Menyediakan dataset kuis yang terstruktur untuk **Kelas X, XI, dan XII** di 12 rumpun mata pelajaran SMA/MA/SMK.
- **Tantangan Adaptif & Pemecahan Masalah**: Menguji pemahaman siswa secara dinamis melalui tingkat kesulitan _Easy, Standard, Hard_, event _Probability Storm_, serta _Special Mystery Tiles_.

---

## 🎮 Game Concept & UI Flow

Platform menggunakan arsitektur _Single Page Application (SPA)_ dengan alur navigasi permainan yang terstruktur:

$$\text{Main Menu (Screen 1)} \rightarrow \text{Pilih Player (2-4)} \rightarrow \text{Pilih Kelas (X, XI, XII)} \rightarrow \text{Pilih Mapel} \rightarrow \text{Pilih Kesulitan (Easy, Std, Hard)} \rightarrow \text{Board Game (Screen 3)}$$

### Alur Navigasi Utama:

1. **Screen 1 (Main Menu):** Pilihan Memulai Game, Info Petunjuk, atau Pengaturan Audio.
2. **Screen 2 (Setup Menu):**
   - **Jumlah Pemain:** 2 Player, 3 Player, atau 4 Player.
   - **Pilihan Kelas:** Kelas X, Kelas XI, atau Kelas XII.
   - **Pilihan Mata Pelajaran:** Grid kartu dinamis sesuai kurikulum kelas aktif.
   - **Tingkat Kesulitan Game:** Mudah (_Easy_), Standar (_Standard_), atau Sulit (_Hard_).
3. **Screen 3 (Board Game):** Papan 100 kotak interaktif dengan animasi pion, indikator giliran, event Badai Probabilitas, Kotak Ungu (Misteri), dan modal kuis pendidikan.

---

## ✨ Main Features

### 👥 Player & Game Setup

- **Multi-Player Support**: Bermain dalam kelompok 2, 3, atau 4 pemain secara bergantian (_Turn-based_).
- **Custom Player Names & Avatars**: Kustomisasi nama pemain dan visualisasi warna pion.

### 📚 Subject & Class Selection System

- **Dynamic Subject Grid**: Mata pelajaran di-render secara dinamis berdasarkan kelas yang dipilih.
- **Cakupan Rumpun Pelajaran**:
  - **Kelas X (12 Mapel)**: Bahasa Indonesia, Bahasa Inggris, Biologi, Ekonomi, Fisika, Geografi, Informatika, Kimia, Matematika, PKN, Sejarah, Sosiologi.
  - **Kelas XI (5 Mapel)**: Bahasa Indonesia, Bahasa Inggris, Informatika, Matematika, PKN.
  - **Kelas XII (5 Mapel)**: Bahasa Indonesia, Bahasa Inggris, Informatika, Matematika, PKN.

### 📱 AR Dadu Mandiri (App Pendamping)

Proyek ini menyediakan panduan aplikasi pendamping berbasis Android untuk memvisualisasikan dadu 3D melalui teknologi _Image Tracking_, dilengkapi penjelasan karakteristik angka dan link materi pembelajaran interaktif.

### 🌪️ Probability Storm (Badai Probabilitas)

Event otomatis berkala (Default: 3 Menit) yang memicu kompetisi antar seluruh pemain:

- **Audio Immersif**: Countdown tegang 30 detik terakhir diikuti suara sirine badai.
- **Turn Competition**: Semua pemain diberikan soal kuis secara bergantian untuk memperebutkan bonus 3 langkah dan menghentikan badai.

### 🏆 Achievement, Guardian Gate & Sertifikat Digital

- **Guardian Gate**: Pemain wajib menjawab soal kuis saat mendarat di tangga atau ular. Jawaban benar memungkinkan naik tangga atau selamat dari patukan ular.
- **Gelar Dinamis & Sertifikat HD**: Di akhir permainan, pemenang dianugerahi gelar unik (_Sang Arsitek Angka, Sang Pemecah Misteri, Penyintas Ular_, dll) dan sertifikat HD PNG yang dapat diunduh langsung via `html2canvas`.

### 🎶 Audio Ducking & Nuansa Lokal

- **Kultur Sunda**: Instrumen musik Sunda sebagai identitas audio permainan.
- **Smart Ducking Logic**: Volume musik latar otomatis mengecil (_Duck_) saat modal kuis muncul agar pemain dapat berkonsentrasi.

---

## 📊 Difficulty System vs. 🟣 Mystery Event

> **Catatan Penting mengenai Perbedaan Konsep:**
>
> - **Difficulty (Pilihan Kesulitan):** Ditentukan pemain saat setup permainan (`Easy`, `Standard`, atau `Hard`).
> - **Mystery (Special Gameplay Event):** **BUKAN** pilihan tingkat kesulitan. Mystery adalah _special event / hidden gem_ yang dipicu saat pemain mendarat di **Kotak Ungu (_Purple Tile_)** di papan permainan.

```text
GAME CONFIGURATION (Setup)
└── Difficulty Selection
    ├── 🟢 Easy (Mudah)
    ├── 🟡 Standard (Standar)
    └── 🔴 Hard (Sulit)

GAMEPLAY EVENT (Di Papan)
└── 🟣 Mystery / Purple Tile
    └── Special Mystery Question (mysteryQuestion.json)
        ├── Benar : Random Reward (Maju 2–5 Langkah)
        └── Salah : Penalti (Mundur 1 Langkah)
```

---

## ❓ Question System & Schema

Engine kuis mendukung 3 tipe soal utama dengan evaluasi pintar:

1. **Multiple Choice (Pilihan Ganda)**: Evaluasi berbasis index (_zero-based_).
2. **True / False (Benar / Salah)**: Evaluasi boolean.
3. **Essay (Uraian / Isian)**:
   - `input_type: "text"`: Evaluasi kalimat toleran terhadap kapitalisasi, spasi berlebih, dan tanda baca.
   - `input_type: "math"`: Evaluasi matematika pintar tanpa library eksternal berat. Mengidentifikasi bahwa `1/2`, `0.5`, `0,5`, `2/4`, `3/6`, dan LaTeX `\frac{1}{2}` bernilai **sama**.
   - `input_type: "set"`: Evaluasi himpunan matematika acak (misal `{1, 2, 3}` vs `{3, 2, 1}`).

### JSON Schema Standard:

```json
{
  "difficulty": "standard",
  "multiple_choice": [
    {
      "id": "S-MC-01",
      "question": "Berapakah hasil dari 2 + 2?",
      "options": ["3", "4", "5"],
      "answer": 1,
      "time_limit": 30,
      "explanation": "2 + 2 = 4"
    }
  ],
  "true_false": [
    {
      "id": "S-TF-01",
      "question": "Bumi berbentuk bulat.",
      "answer": true,
      "time_limit": 20,
      "explanation": "Bumi merupakan geoid."
    }
  ],
  "essay": [
    {
      "id": "S-ES-01",
      "question": "Berapakah nilai dari 1/2 + 1/2?",
      "answer": "1",
      "input_type": "math",
      "time_limit": 45,
      "explanation": "1/2 + 1/2 = 1"
    }
  ]
}
```

---

## ⚙️ Question Engine Architecture

`QuestionEngine` pada `script.js` dibangun menggunakan arsitektur modular yang terpisah dari _Game Engine_ Ular Tangga:

1. **`QuestionEngine.Loader`:** Mengambil file JSON secara dinamis berparameter `loadQuestions(classId, subjectId, difficultyId)`.
2. **`QuestionEngine.Manager`:** Mengelola _question pool_ dan memilih soal acak berdasarkan tipe kotak (`easy`, `standard`, `hard`, `mystery`).
3. **`QuestionEngine.Renderer`:** Merender UI modal, metadata mapel & kelas, timer countdown, serta tipe input jawaban.
4. **`QuestionEngine.Validator`:** Menangani validasi pilihan ganda, boolean, kalimat essay, pecahan matematika, dan himpunan.
5. **`QuestionEngine.ScoreManager`:** Mencatat statistik benar, salah, _streak_, _mystery solved_, dan _storm wins_.
6. **`QuestionEngine.TimerManager`:** Mengelola interval countdown timer secara aman tanpa kebocoran memori.

---

## 📁 Project Structure

```text
snakes-and-ladders-V1/
├── index.html                  # Single Page Application Markup
├── style.css                   # Responsive CSS UI/UX Design System
├── script.js                   # Game Engine & Modular QuestionEngine Logic
├── audio/                      # Effects & BGM Sound Assets
│   ├── Sunda.mp3
│   ├── Sabilulungan.mp3
│   ├── Sirine.mp3
│   ├── Countdown.mp3
│   ├── dice.mp3
│   ├── drop.mp3
│   ├── ladder.mp3
│   ├── snake.mp3
│   └── success.mp3
├── question/                   # Dynamic Question Dataset Architecture
│   ├── kelas_x/                # Dataset Kelas X (12 Rumpun Mata Pelajaran)
│   ├── kelas_xi/               # Dataset Kelas XI (5 Rumpun Mata Pelajaran)
│   └── kelas_xii/              # Dataset Kelas XII (5 Rumpun Mata Pelajaran)
└── README.md                   # Technical Manual & Documentation
```

---

## ➕ Extensibility (Menambahkan Mapel / Kelas Baru)

### Cara Menambahkan Mata Pelajaran Baru:

1. Buat folder baru: `question/kelas_x/seni_budaya/`
2. Buat 4 file JSON soal: `easyQuestion.json`, `standarQuestion.json`, `hardQuestion.json`, dan `mysteryQuestion.json`.
3. Daftarkan via API:
   ```javascript
   QuestionEngine.registerSubject("kelas_x", {
     id: "seni_budaya",
     name: "Seni Budaya",
     icon: "🎨",
   });
   ```

### Cara Menambahkan Kelas Baru:

1. Daftarkan kelas: `QuestionEngine.registerClass("kelas_xiii", "Kelas XIII");`
2. Buat folder `question/kelas_xiii/matematika/` dan tambahkan 4 file JSON soal.

---

## 🛠️ Technologies Used

- **HTML5 & CSS3**: Formatisasi SPA dan sistem UI _glassmorphism_ responsif.
- **JavaScript (Vanilla ES6+)**: _Engine_ permainan, algoritma acak, _Question Engine_, dan manajemen audio.
- **MathLive**: Input notasi matematika interaktif berbasis LaTeX.
- **html2canvas**: Rendering DOM ke gambar PNG untuk ekspor Sertifikat Pemenang.
- **Web Audio API Logic**: Sistem audio _fading_ dan _ducking_ otomatis.

---

## 🚀 How to Run

1. _Clone_ repository ini:
   ```bash
   git clone https://github.com/icanxPrograming/Game-Ular-Tangga-Edukatif-dan-Interaktif-Berbasis-Web.git
   ```
2. Buka folder project.
3. Jalankan file `index.html` menggunakan browser (Sangat disarankan menggunakan ekstensi **Live Server** di VS Code agar fitur _fetch JSON_ berjalan lancar tanpa kendala _CORS/security_ browser).

---

## 📝 Development History

### Initial Version (Base Project)

- Berfokus pada satu mata pelajaran/topik spesifik.
- Alur navigasi sederhana: `Menu -> Player -> Difficulty -> Game`.

### Major Expansion (Current Version)

- **Multi-Subject & Multi-Class Platform**: Perluasan navigasi menjadi `Menu -> Player -> Class -> Subject -> Difficulty -> Game`.
- **Modular QuestionEngine Architecture**: Pemisahan penuh antara Game Engine Ular Tangga dan Question Engine Kuis (6 Sub-modul).
- **Expanded Question Datasets**: Pembentukan 84 file JSON kuis terstruktur di 19 direktori pelajaran SMA (Kelas X, XI, XII).
- **Smart Math & Text Evaluator**: Parser matematika internal yang mengenali kesetaraan pecahan (`1/2`, `0.5`, `2/4`, `3/6`, `\frac{1}{2}`).
- **Hardened Validation & Error Handling**: Penanganan 10 potensi kesalahan data kuis dengan proteksi _fallback_ otomatis.

---

## 🙏 Credits & Acknowledgments

Proyek ini dikembangkan untuk tujuan pendidikan dan peningkatan minat belajar siswa. Merupakan hasil modifikasi dan pengembangan komprehensif dari _base project_ original milik **[Yashksaini](https://github.com/yashksaini)**.

---

_Dikembangkan dengan standar arsitektur modular tinggi untuk platform pembelajaran interaktif._
