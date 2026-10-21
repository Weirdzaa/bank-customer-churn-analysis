# Analisis Churn Nasabah Bank: Siapa yang Paling Berisiko Pergi?

Project analisis data untuk mencari tahu nasabah bank seperti apa yang paling berisiko berhenti (churn), lalu menyusun rekomendasi retensi yang bisa dijalankan.

## Ringkasan

Dari 10.000 nasabah, **2.038 (20,38%) churn**. Analisis ini membedah segmen nasabah berdasarkan negara, gender, usia, jumlah produk, keaktifan, saldo, komplain, dan skor kepuasan untuk menemukan kelompok dengan risiko tertinggi.

## Pertanyaan Bisnis

1. Berapa churn rate keseluruhan, dan di negara/gender mana paling tinggi?
2. Kelompok usia mana yang paling berisiko churn?
3. Bagaimana pengaruh jumlah produk dan keaktifan nasabah?
4. Apakah nasabah bersaldo besar lebih rentan pergi?
5. Apa peran komplain dan skor kepuasan terhadap churn?

## Dataset

- **Nama:** Bank Customer Churn Records (Kaggle)
- **Ukuran:** 10.000 baris, 18 kolom (15 kolom dipakai setelah kolom identitas dibuang)
- **Target:** `Exited` (1 = churn, 0 = bertahan)
- **Kualitas data:** tidak ada data kosong dan tidak ada duplikat

## Tools

Python (pandas, matplotlib), Google Colab

## Isi Repo

| File | Keterangan |
|---|---|
| `bank-churn-analysis.ipynb` | Notebook analisis lengkap (kode, grafik, temuan) |
| `Customer-Churn-Records.csv` | Dataset |
| `README.md` | Ringkasan project |

## Temuan Utama

| Area | Temuan |
|---|---|
| Usia | Churn naik tajam setelah usia 40 dan puncaknya di usia 50-59 (56,04%) |
| Jumlah produk | 2 produk paling loyal (7,60%), 1 produk 27,71%, 3-4 produk hampir semuanya churn (82,71% dan 100%, hanya 326 nasabah) |
| Keaktifan | Nasabah tidak aktif churn 26,87%, hampir dua kali lipat nasabah aktif (14,27%) |
| Saldo | Nasabah bersaldo tinggi yang tidak aktif (1.569 orang) churn 31,23% dan menyumbang 24,0% dari seluruh churn |
| Negara | Germany 32,44%, hampir dua kali lipat France (16,17%) dan Spain (16,67%) |
| Gender | Perempuan 25,07%, laki-laki 16,47% |
| Dampak finansial | Saldo milik nasabah churn mencapai 24,28% dari total saldo |
| Komplain | Korelasi dengan churn 0,996, kemungkinan data leakage (dicatat setelah nasabah memutuskan pergi) |
| Skor kepuasan | Tidak berhubungan dengan churn (korelasi -0,006) |

Tingginya churn di Germany tidak dijelaskan oleh usia, keaktifan, gender, jumlah produk, atau gaji, karena Germany tertinggi di setiap kelompok tersebut. Penyebabnya kemungkinan berada di luar variabel dataset ini.

## Rekomendasi

1. Prioritaskan program retensi untuk nasabah usia 40-59 tahun, terutama 50-59 tahun.
2. Jalankan kampanye pengaktifan kembali untuk nasabah tidak aktif, dimulai dari nasabah bersaldo tinggi.
3. Uji coba cross-selling untuk mendorong nasabah 1 produk ke produk kedua.
4. Tinjau paket dan proses penjualan untuk nasabah 3-4 produk sebelum mendorong lebih dari 2 produk.
5. Selidiki penyebab churn di Germany, perbaiki pencatatan komplain, dan evaluasi cara mengukur skor kepuasan.

## Keterbatasan

- Korelasi bukan berarti sebab-akibat.
- Waktu pencatatan komplain tidak diketahui, sehingga dugaan data leakage tidak bisa dipastikan.
- Dataset tidak memuat alasan nasabah pergi, tanggal churn, mata uang, maupun keuntungan per nasabah.
- Kelompok 3-4 produk kecil (326 nasabah), jadi angkanya perlu dibaca hati-hati.
- Analisis membandingkan faktor satu per satu dan belum memakai model prediktif.

## Cara Menjalankan

1. Buka notebook `bank-churn-analysis.ipynb` di [Google Colab](https://colab.research.google.com).
2. Jalankan sel pertama, lalu upload file `Customer-Churn-Records.csv` saat diminta.
3. Jalankan sel berikutnya secara berurutan dari atas ke bawah.

## Pengembangan Selanjutnya

- Membuat model prediksi churn (misalnya regresi logistik) tanpa kolom komplain
- Membuat dashboard di Power BI atau Looker Studio
- Menambah analisis SQL untuk pertanyaan yang sama

## Penulis

Nama Anda | [LinkedIn](https://linkedin.com/in/username-anda) | email@anda.com
