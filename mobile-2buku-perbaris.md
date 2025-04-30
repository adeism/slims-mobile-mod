---

## Tutorial: Perbaikan Tata Letak Mobile untuk Koleksi Populer di Template Default SLiMS

**Target:** Pengguna SLiMS (Pustakawan, Administrator) yang menggunakan template OPAC default (Classic).

**Tujuan:** Menjelaskan perbaikan tata letak pada bagian "Koleksi Populer" agar lebih ramah pengguna (user-friendly) di perangkat mobile.

---

### Latar Belakang Masalah

Template default SLiMS (sering disebut tema "Classic") memiliki bagian untuk menampilkan koleksi yang paling sering dipinjam atau populer ("Popular among our collections"). Meskipun berfungsi dengan baik di layar desktop, tata letaknya kurang optimal saat diakses melalui perangkat mobile atau layar yang lebih kecil.

**Masalah Spesifik:**

Pada tampilan mobile, setiap item koleksi (sampul buku beserta judulnya) ditampilkan dalam **satu baris penuh**. Ini berarti pengguna harus melakukan *scroll* (menggulir layar) cukup panjang ke bawah untuk melihat semua koleksi populer, terutama jika jumlah koleksi yang ditampilkan cukup banyak. Tata letak ini kurang efisien dalam memanfaatkan ruang layar mobile yang terbatas.

### Sebelum Perbaikan

Berikut adalah gambaran bagaimana bagian "Koleksi Populer" terlihat di layar mobile *sebelum* perbaikan diterapkan:

*   Setiap item koleksi (sampul dan judul) memakan seluruh lebar layar.
*   Item-item tersusun secara vertikal, satu di bawah yang lain.
*   Membutuhkan banyak scroll untuk melihat beberapa item saja.

```
+-----------------------------------+
| [ Gambar Sampul Buku 1      ]   |
|   Judul Buku 1 yang Panjang     |
+-----------------------------------+
| [ Gambar Sampul Buku 2      ]   |
|   Judul Buku 2                  |
+-----------------------------------+
| [ Gambar Sampul Buku 3      ]   |
|   Judul Buku 3                  |
+-----------------------------------+
|           ... (Scroll) ...      |
+-----------------------------------+
```

*(Idealnya, sertakan screenshot nyata dari tampilan sebelum perbaikan di sini)*

**[Gambar Screenshot Sebelum Perbaikan]**

### Mengapa Perubahan Ini Dilakukan?

Tata letak satu item per baris di mobile:

1.  **Kurang Efisien:** Membuang-buang ruang layar yang berharga.
2.  **Kurang Nyaman:** Pengguna harus menggulir lebih banyak untuk melihat variasi koleksi.
3.  **Kurang Menarik Secara Visual:** Tampilan terasa terlalu "memanjang" ke bawah.

Tujuan perbaikan ini adalah untuk meningkatkan pengalaman pengguna (User Experience/UX) saat mengakses OPAC SLiMS melalui perangkat mobile.

### Sesudah Perbaikan

Dengan perbaikan yang telah diterapkan, tata letak bagian "Koleksi Populer" di layar mobile kini menjadi **dua kolom**.

*   Setiap item koleksi sekarang hanya memakan setengah lebar layar.
*   Dua item koleksi ditampilkan berdampingan dalam satu baris.
*   Pengguna dapat melihat lebih banyak koleksi dalam satu layar tanpa perlu banyak scroll.

```
+-----------------+-----------------+
| [ Sampul Buku 1]| [ Sampul Buku 2]|
|   Judul Buku 1  |   Judul Buku 2  |
+-----------------+-----------------+
| [ Sampul Buku 3]| [ Sampul Buku 4]|
|   Judul Buku 3  |   Judul Buku 4  |
+-----------------+-----------------+
| [ Sampul Buku 5]| [ Sampul Buku 6]|
|   Judul Buku 5  |   Judul Buku 6  |
+-----------------+-----------------+
|       ... (Scroll lebih sedikit)...|
+-----------------+-----------------+
```

*(Idealnya, sertakan screenshot nyata dari tampilan sesudah perbaikan di sini)*

**[Gambar Screenshot Sesudah Perbaikan]**

### Detail Teknis (Untuk yang Ingin Tahu)

Perubahan ini dilakukan pada file JavaScript yang mengelola komponen tampilan koleksi di template default:

*   **File:** `template/default/assets/js/app.js`
*   **Komponen Vue.js:** `slims-book`
*   **Perubahan:** Kelas CSS Tailwind `w-48` (yang menetapkan lebar tetap) pada elemen pembungkus setiap item buku diganti dengan kelas responsif `w-1/2 md:w-1/5`.
    *   `w-1/2`: Membuat lebar item menjadi 50% di layar terkecil (mobile), sehingga dua item muat per baris.
    *   `md:w-1/5`: Membuat lebar item menjadi 20% (lima item per baris) di layar medium (`md`) dan yang lebih besar. Jumlah kolom untuk layar besar ini bisa disesuaikan (misal: `md:w-1/4` untuk 4 kolom).

### Bagaimana Mendapatkan Perbaikan Ini?

Kode sumber SLiMS dalam repositori ini **sudah mencakup** perbaikan tata letak mobile untuk bagian Koleksi Populer. Untuk mendapatkan manfaat dari perbaikan ini:

1.  **Gunakan Versi Ini:** Pastikan Anda menggunakan versi SLiMS yang berasal dari repositori ini.
2.  **Update Template:** Jika Anda sebelumnya menggunakan SLiMS versi standar, Anda perlu memperbarui file `template/default/assets/js/app.js` dengan versi yang ada di repositori ini.
3.  **Bersihkan Cache:** Setelah memperbarui file, pastikan untuk membersihkan cache browser Anda (Ctrl+Shift+R atau Cmd+Shift+R) agar perubahan dapat terlihat.

### Kesimpulan

Perbaikan kecil pada tata letak bagian Koleksi Populer ini memberikan peningkatan signifikan pada pengalaman pengguna di perangkat mobile. Tampilan menjadi lebih rapi, efisien, dan memudahkan pengguna untuk menjelajahi koleksi unggulan perpustakaan Anda.

---
