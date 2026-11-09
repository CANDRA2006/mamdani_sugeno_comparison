# Perbandingan Sistem Inferensi Logika Fuzzy: Mamdani vs. Sugeno

Repositori ini berisi implementasi dan analisis komparatif antara dua metode inferensi fuzzy yang paling populer: **Metode Mamdani** (*Max-Min / Centroid*) dan **Metode Sugeno** (*Takagi-Sugeno-Kang / Weighted Average*).

Proyek ini bertujuan untuk membandingkan kinerja, karakteristik keluaran (*output*), akurasi, serta efisiensi komputasi dari kedua metode tersebut dalam menyelesaikan kasus keputusan atau sistem kontrol tertentu.

---

## Latar Belakang

Logika Fuzzy (*Fuzzy Logic*) merupakan pendekatan komputasi berdasarkan derajat kebenaran (*degree of truth*) daripada logika boolean konvensional (0 atau 1). Dua model inferensi fuzzy yang paling sering digunakan adalah:

1. **Mamdani (Max-Min / Centroid):** Menggunakan fungsi keanggotaan logika fuzzy baik pada premis (*antecedent*) maupun konsekuen (*consequent*). Proses defuzzifikasi umumnya menggunakan metode *Centroid* (titik berat). Sangat intuitif dan cocok untuk sistem yang membutuhkan interpretasi manusia.
2. **Sugeno (Takagi-Sugeno-Kang / TSK):** Menggunakan fungsi keanggotaan pada premis, namun konsekuennya berupa konstanta atau fungsi linier dari variabel input. Proses defuzzifikasi menggunakan rata-rata terbobot (*Weighted Average*). Sangat efisien secara komputasi dan cocok untuk sistem kontrol otomatis.

---

## Perbandingan Singkat Mamdani vs. Sugeno

| Parameter | Metode Mamdani | Metode Sugeno |
| :--- | :--- | :--- |
| **Output / Konsekuen** | Himpunan Fuzzy (Kualitatif / Linguistik) | Fungsi Linier atau Konstanta (Kuantitatif) |
| **Defuzzifikasi** | Kompleks (Centroid, Bisector, MOM, dll.) | Sederhana (Weighted Average / Sum) |
| **Beban Komputasi** | Lebih Tinggi (Integrasi area fuzzy) | Lebih Rendah & Sangat Cepat |
| **Interpretasi** | Sangat mudah dipahami manusia | Lebih abstrak / matematis |
| **Kesesuaian** | Sistem Pakar, Pengambilan Keputusan | Sistem Kontrol Otomatis, ANFIS, Real-time |

---

## Fitur Utama

-  **Fuzzifikasi & Membership Function:** Pembentukan kurva keanggotaan (Segitiga, Trapesium, Gaussian).
-  **Evaluasi Rule Base:** Penerapan aturan *IF-THEN* secara konsisten pada kedua metode.
-  **Defuzzifikasi Engine:** Implementasi *Centroid* untuk Mamdani dan *Weighted Average* untuk Sugeno.
- **Visualisasi Grafis:** Grafik fungsi keanggotaan, kurva daerah fuzzy, dan surface plot.
-  **Analisis Kinerja:** Komparasi nilai luaran (*crisp output*) dan waktu eksekusi.

---

## Prasyarat & Instalasi

### Prasyarat
- **Python 3.8+**
- **pip** (Package Manager Python)

### Langkah Instalasi

1. **Clone repositori ini:**
   ```bash
   git clone https://github.com/CANDRA2006/mamdani_sugeno_comparison.git
   cd mamdani_sugeno_comparison
   ```

2. **Buat dan aktifkan virtual environment:**
   ```bash
   python -m venv venv
   # Linux/macOS:
   source venv/bin/activate
   # Windows:
   .\venv\Scripts\activate
   ```

3. **Install dependensi yang diperlukan:**
   ```bash
   pip install -r requirements.txt
   ```

---


##  Metodologi

1. **Fuzzifikasi:** Konversi nilai input *crisp* menjadi derajat keanggotaan fuzzy $\mu(x)$.
2. **Evaluasi Aturan:** Pengaplikasian operator logika (AND/OR) pada aturan *IF-THEN*.
3. **Inference Engine:**
   - **Mamdani:** Operasi MIN untuk implikasi dan MAX untuk agregasi.
   - **Sugeno:** Perhitungan bobot implikasi $w_i$ dan kombinasi linier $z_i$.
4. **Defuzzifikasi:**
   - **Mamdani (Centroid):**
     $$Z^* = \frac{\int z \cdot \mu(z) \, dz}{\int \mu(z) \, dz}$$
   - **Sugeno (Weighted Average):**
     $$Z^* = \frac{\sum_{i=1}^{N} w_i \cdot z_i}{\sum_{i=1}^{N} w_i}$$

---

---

## Lisensi

Proyek ini dilisensikan di bawah [MIT License](LICENSE).

---
