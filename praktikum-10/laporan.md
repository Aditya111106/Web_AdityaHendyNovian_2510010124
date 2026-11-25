# Laporan Praktikum Pertemuan 10 — Pemrograman Web 1

Nama : Aditya Hendy Novian  
NIM  : 2510010124
Kelas: 3B TI

> Lengkapi pengamatan berdasarkan uji browser, masukkan screenshot sendiri, dan isi skor Lighthouse sesuai hasil yang benar-benar diperoleh.

## Percobaan 1 — Navbar Lab

| No | Eksperimen | Pengamatan |
|---|---|---|
| 1 | Class `#menuLab` dan nilai `aria-expanded` saat terbuka | Saat dibuka, elemen memiliki class `collapse navbar-collapse show` dan tombol bernilai `aria-expanded="true"`. Saat ditutup, class `show` hilang dan nilainya `false`. |
| 2 | Hamburger di 1000 px dengan `navbar-expand-lg` | Hamburger tidak tampil karena 1000 px ≥ 992 px; menu ditampilkan berjajar. |
| 3 | Perilaku di 800 px: `-md` / tanpa sufiks / tanpa class expand | `navbar-expand-md` menampilkan menu berjajar; `navbar-expand` selalu berjajar; tanpa class expand menu tetap terlipat. |
| 4 | `data-bs-target` salah ketik | Tombol tidak membuka menu karena target tidak cocok dengan ID elemen collapse. Console bisa saja tidak menampilkan error. |
| 5 | Tanpa JS bundle | Navbar tetap terlihat, tetapi hamburger dan dropdown tidak berfungsi karena JavaScript Bootstrap tidak dimuat. |
| 6 | `bg-dark` tanpa dan dengan `data-bs-theme="dark"` | `bg-dark` saja dapat membuat teks menu sulit terbaca. Tema dark menyesuaikan teks dan ikon agar terang. |
| 7 | `sticky-top` vs `fixed-top` | `sticky-top` menempel saat digulir dan tetap di aliran dokumen. `fixed-top` keluar dari aliran dokumen sehingga judul dapat tertutup navbar. |

## Percobaan 2 — Buttons & Badges

| No | Eksperimen | Pengamatan |
|---|---|---|
| 1 | Kelompok Batal–Simpan di 375 px dan 1000 px | Pada 375 px tombol bertumpuk selebar penuh; pada 1000 px tombol sebaris dan rata kanan. |
| 2 | Elemen nonaktif yang masih bisa difokus dengan Tab | Tombol `disabled` dilewati Tab. Tautan yang hanya memakai class `disabled` tetapi masih memiliki `href` tetap dapat difokus dan diaktifkan. Tautan tanpa `href` dan `aria-disabled="true"` tidak menerima fokus. |
| 3 | Kontras `text-bg-warning` vs `bg-warning` | `text-bg-warning` memasangkan teks gelap dengan latar kuning. `bg-warning` saja dapat mewarisi teks putih sehingga kontras rendah. |
| 4 | Nama tombol Notifikasi dengan dan tanpa `visually-hidden` | Dengan `visually-hidden`, nama tombol dibaca “Notifikasi 3 notifikasi belum dibaca”; tanpa itu hanya “Notifikasi 3”. |

## Percobaan 3 — Tipografi

| Class lama | Utilitas pengganti | Tampilan sama? |
|---|---|---|
| `.judul-besar` | `display-5 text-center` | Ya, mendekati |
| `.pembuka` | `lead text-body-secondary text-center` | Ya, mendekati |
| `.label` | `text-uppercase fw-bold small` | Hampir sama; letter-spacing diabaikan |
| `.catatan` | `small fst-italic` | Ya |
| `.nim` | `font-monospace` | Ya |
| Temuan Lighthouse untuk `<h4>` | Heading melompat dari h1 langsung ke h4. Pertahankan h2 dan gunakan class `h4` jika ingin tampilan lebih kecil. | Struktur heading diperbaiki |

Simpan tangkapan layar sebelum dan sesudah sebagai `p3-tipografi/sebelum.png` dan `p3-tipografi/sesudah.png`.
