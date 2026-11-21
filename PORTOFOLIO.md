# PORTOFOLIO INDIVIDU
## Project Akhir Sistem Operasi 5A — Sistem Otomasi Backup dan Pemulihan Data Linux

### 1. Identitas

| Keterangan | Informasi |
|---|---|
| Nama | Muhamad Afwan Imam Nasuha |
| NIM | 2510512195 |
| Program Studi | S1 Sistem Informasi |
| Perguruan Tinggi | UPN Veteran Jakarta |
| Kelompok | Kelompok 1 |
| Kelas | E |
| Mata Kuliah | Sistem Operasi |
| Proyek | 5A — Sistem Otomasi Backup dan Pemulihan Data Linux |
| Peran | Anggota 1 — Validasi Sumber dan Parameter |

### 2. Asal Proyek

Proyek ini merupakan hasil kerja kelompok yang dikembangkan bersama lima anggota lainnya untuk memenuhi tugas akhir mata kuliah Sistem Operasi.

Repository utama kelompok:

[Kelompok 1 Project 5A — Repository Utama](https://github.com/Kelompok-1-Project-5A-Kelas-E/automation-backup-and-recovery-data)

Repository pribadi:

[AfwanNasuha — Personal Portfolio Fork](https://github.com/AfwanNasuha/automation-backup-and-recovery-data-portfolio)

Repository pribadi ini merupakan fork dari repository utama kelompok. Pengembangan proyek dilakukan secara kolaboratif dengan pembagian tanggung jawab teknis kepada setiap anggota.

### 3. Kontribusi Pribadi

Saya bertanggung jawab sebagai Anggota 1 dengan fokus pekerjaan pada validasi sumber, direktori tujuan, parameter, dan hak akses direktori.

Kontribusi yang saya kerjakan meliputi:

1. Pengembangan dan pemeriksaan modul `scripts/validation.sh` untuk memvalidasi parameter serta direktori sumber dan tujuan sebelum proses backup dijalankan.
2. Pengujian kondisi positif dan negatif pada modul validasi.
3. Pelaksanaan pengujian utama T01–T03 secara langsung pada VM Ubuntu Server kelompok.
4. Pelaksanaan pengujian tambahan V01–V06 menggunakan CachyOS dan akun non-root.
5. Penyusunan dokumentasi hasil pengujian serta pengelolaan bukti pengujian.
6. Memelihara repository GitHub kelompok, mengelola struktur direktori dan berkas, memperbarui README, serta menyusun dan merapikan dokumentasi teknis dan bukti pengujian.

### 4. Skenario dan Hasil Pengujian Individu

Pengujian utama dilaksanakan pada VM Ubuntu Server kelompok.

| ID | Skenario | Hasil Aktual | Exit Status | Status |
|---|---|---|---:|---|
| T01 | Sumber dan tujuan valid | Validasi berhasil | 0 | Lulus |
| T02 | Sumber tidak ditemukan | Direktori sumber tidak ditemukan | 3 | Lulus |
| T02 Tambahan | Sumber berupa file, bukan direktori | Sumber bukan direktori | 3 | Lulus |
| T03 | Parameter wajib tidak diberikan | Parameter tidak lengkap ditolak | 2 | Lulus |

Pengujian tambahan V01–V06 dilaksanakan secara lokal menggunakan CachyOS.

Cakupan pengujian tambahan meliputi:
- Parameter kosong.
- Sumber berupa file biasa.
- Direktori tujuan tidak ditemukan.
- Penggunaan direktori valid oleh akun non-root.
- Sumber tanpa izin akses.
- Direktori tujuan tanpa izin tulis.

Pengujian lokal digunakan sebagai bukti tambahan dan dibedakan dari hasil pengujian resmi pada VM Ubuntu Server.

### 5. Bukti Kontribusi

Berkas yang berkaitan dengan kontribusi pribadi:

| Lokasi | Keterangan |
|---|---|
| `scripts/validation.sh` | Modul validasi sumber dan tujuan |
| `tests/anggota1-uji-validasi.md` | Dokumentasi pengujian tambahan |
| `evidence/anggota1-uji-validasi.txt` | Ringkasan hasil pengujian |
| `evidence/01-validation/` | Bukti pengujian lokal |
| `evidence/07-ubuntu-server-demo/01-validation/` | Bukti resmi T01–T03 pada Ubuntu Server |

Riwayat kontribusi Git:

[Riwayat commit Afwan pada repository utama](https://github.com/Kelompok-1-Project-5A-Kelas-E/automation-backup-and-recovery-data/commits/main/?author=AfwanNasuha)

[Riwayat commit repository pribadi](https://github.com/AfwanNasuha/automation-backup-and-recovery-data-portfolio/commits/main)

### 6. Analisis Konsep Sistem Operasi

Kontribusi saya pada proyek ini berkaitan dengan beberapa konsep Sistem Operasi.

**a. Process dan Exit Status**

Modul validasi dijalankan melalui Bash sebagai sebuah proses. Hasil pemeriksaan dikomunikasikan melalui exit status yang digunakan untuk menentukan apakah proses backup dapat dilanjutkan atau harus dihentikan.

**b. Filesystem**

Validasi memeriksa kondisi direktori sumber dan tujuan sebelum operasi pencadangan dilakukan. Pemeriksaan ini membantu mencegah proses backup dijalankan dengan lokasi sumber atau tujuan yang tidak sesuai.

**c. Protection dan Permission**

Pengujian tambahan menggunakan akun non-root dilakukan untuk memeriksa perilaku validasi ketika pengguna memiliki hak akses berbeda terhadap direktori sumber maupun tujuan. Hal ini berkaitan dengan mekanisme permission dan kontrol akses pada Linux.

**d. Input Validation dan Error Handling**

Pemeriksaan parameter memastikan script menerima jumlah dan nilai parameter yang sesuai. Kondisi yang tidak valid ditolak menggunakan pesan kesalahan dan exit status yang sesuai dengan skenario pengujian.

Kontribusi individual saya berfokus pada validasi. Konsep sinkronisasi, monitoring, dan pemulihan dibahas dalam konteks integrasi sistem kelompok sesuai modul yang dikerjakan anggota lainnya.

### 7. Kendala dan Penyelesaian

Salah satu kendala yang ditemukan selama penggunaan modul adalah direktori tujuan belum tersedia ketika validasi dijalankan.

Kondisi tersebut menghasilkan pesan `Direktori tujuan tidak ditemukan` dengan exit status 5.

Penyelesaian dilakukan dengan memuat konfigurasi lingkungan demonstrasi melalui `tests/demo/demo-env.sh`, kemudian membuat direktori tujuan menggunakan `mkdir -p "$DEST"` sebelum menjalankan validasi.

Pengalaman ini membantu saya memahami pentingnya urutan konfigurasi lingkungan, pemeriksaan direktori, dan eksekusi modul dalam penggunaan sistem berbasis shell script.

### 8. Refleksi

Melalui proyek ini, saya memperoleh pengalaman dalam mengembangkan dan menguji shell script pada lingkungan Linux, memahami pemeriksaan direktori serta hak akses, dan menggunakan exit status untuk menangani kondisi keberhasilan maupun kegagalan.

Saya juga memperoleh pengalaman dalam menggunakan Git dan GitHub untuk pengelolaan repository kolaboratif, melakukan penataan struktur direktori, memelihara dokumentasi, serta mengelola bukti pengujian agar dapat ditelusuri.

Proyek ini meningkatkan pemahaman saya mengenai hubungan antara implementasi shell script dengan konsep filesystem, process, input validation, dan protection pada Sistem Operasi.

Ke depannya, saya perlu memperdalam pemahaman mengenai manajemen proses, mekanisme sinkronisasi, serta pengelolaan sistem Linux agar dapat mengembangkan solusi administrasi sistem yang lebih terstruktur.
