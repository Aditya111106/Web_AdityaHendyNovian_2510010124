# Laporan Praktikum Pertemuan 5 — Pemrograman Web 1

**Nama:** Aditya Hendy Novian  
**NIM:** 2510010124  
**Kelas:** 3B TI

> Catatan: tabel berikut berisi hasil yang diharapkan berdasarkan modul. Cocokkan kembali dengan hasil pengukuran dan pengamatan langsung melalui DevTools sebelum dikumpulkan.

## Percobaan 1 — Box Model

| No | Kondisi | Lebar Kotak A (px) | Lebar Kotak B (px) |
|---|---|---:|---:|
| 1 | padding 20px | 350 | 300 |
| 2 | padding 40px | 390 | 300 |

| No | Kondisi | Jarak judul–paragraf (px) |
|---|---|---:|
| 3 | Block biasa | 30 |
| 4 | Di dalam flex column | 50 |

| No | Kondisi `.menu a` | Latar menimpa teks lain? |
|---|---|---|
| 5 | inline (bawaan) | Ya |
| 6 | inline-block | Tidak |

**Pembahasan:** Pada `content-box`, nilai `width` hanya menghitung area konten. Karena itu lebar total Kotak A adalah 300 + 40 + 10 = 350 px. Pada `border-box`, padding dan border sudah termasuk dalam lebar 300 px sehingga Kotak B tetap 300 px. Margin vertikal dua elemen block mengalami margin collapsing, sedangkan di dalam flex column kedua margin tidak bergabung.

## Percobaan 2 — Flexbox Lab

| No | Properti dan nilai | Pengamatan |
|---|---|---|
| 1 | `display: flex` | Ketiga item berubah dari susunan vertikal menjadi berjajar horizontal dalam satu baris. |
| 2 | `justify-content: space-between` | Item A berada di kiri, item C di kanan, dan ruang sisa dibagi di antara item. |
| 3 | `justify-content: space-evenly` | Jarak antaritem dan jarak dari item ke tepi container terlihat sama besar. |
| 4 | `align-items: stretch` vs `center` | Stretch membuat item memenuhi tinggi container, sedangkan center membuat item berada di tengah pada cross axis. |
| 5 | 8 item × 200 px, nowrap vs wrap | No-wrap memaksa item tetap satu baris sehingga item dapat menyusut; wrap memindahkan item ke baris berikutnya. |
| 6 | `.b { flex-grow: 1 }` | Item B mengambil ruang kosong yang tersedia, sedangkan A dan C tetap mengikuti ukuran kontennya. |
| 7 | Lebar A / B / C | A = 200 px, B ≈ 266,7 px, C ≈ 533,3 px (container 1000 px, tanpa gap dan padding horizontal). |
| 8 | `.c { order: -1 }` | Item C tampil paling kiri, tetapi urutan elemen pada HTML tidak berubah. |
| 9 | `.c { margin-left: auto }` | Margin kiri otomatis menyerap ruang kosong sehingga C terdorong ke ujung kanan. |
| 10 | `gap: 24px` | Jarak 24 px muncul di antara item tanpa menambahkan jarak pada tepi container. |

## Percobaan 3 — Positioning

| No | Eksperimen | Pengamatan |
|---|---|---|
| 1 | Header sticky saat digulir | Header mengikuti aliran halaman lalu menempel di bagian atas viewport ketika digulir. |
| 2a | Header fixed tanpa padding-top body | Header keluar dari aliran normal sehingga bagian awal konten tertutup header. |
| 2b | Header fixed dengan padding-top 64px | Konten bergeser ke bawah dan tidak lagi tertutup header. |
| 3 | `.notif` tanpa `position: relative` | Badge berpindah mengikuti leluhur terdekat yang memiliki positioning, yaitu header. |
| 4 | `.lapis-1` z-index 3 lalu `.lapis-2` z-index 5 | Lapis 1 maju ketika diberi z-index 3; setelah Lapis 2 diberi z-index 5, Lapis 2 berada paling depan. |
| 5 | Header z-index 1 | Elemen lapis dengan z-index lebih tinggi dapat menutupi header ketika saling bertumpuk. |
| 6 | Tombol Bantuan di layar 375 px | Tombol tetap berada di kanan bawah viewport ketika halaman digulir. |

## Percobaan 4 — Dashboard

Dashboard SIAKAD Mini dibuat menggunakan struktur HTML5 semantik yang terdiri dari navbar, sidebar, konten utama, dan footer. Navbar menggunakan `position: sticky`, sedangkan tata letak utama menggunakan Flexbox. Sidebar memiliki lebar tetap 240 px dan konten mengisi ruang yang tersisa.

Tambahan tugas mandiri:
1. Profil pengguna berupa avatar bulat 32 px dan teks Admin Prodi di navbar.
2. Menu Pengaturan ditempatkan di dasar sidebar menggunakan `margin-top: auto`.
3. Label Baru ditempatkan di pojok kartu Kelas Hari Ini dengan kombinasi `position: relative` dan `position: absolute`.
4. Tabel jadwal memiliki area gulir maksimal 300 px dan header tabel sticky.

**Tangkapan layar:**
- Desktop 1366 px: `p4-dashboard/desktop.png`
- Mobile 375 px: `p4-dashboard/mobile.png`

Tambahkan tangkapan layar hasil pengujian sendiri dengan nama file tersebut sebelum pengumpulan.

## Jawaban Pertanyaan Analisis

1. `box-sizing: border-box` sering ditulis di awal stylesheet karena membuat perhitungan ukuran elemen lebih mudah. Lebar yang ditentukan sudah mencakup konten, padding, dan border sehingga ukuran elemen lebih mudah dikendalikan dan tidak melebar tanpa disadari.

2. Pada `flex-direction: column`, main axis berubah menjadi vertikal, sedangkan cross axis menjadi horizontal. Karena itu `justify-content: center` mengatur posisi item ke tengah secara vertikal, bukan horizontal.

3. Pada eksperimen 7, lebar A ditetapkan 200 px. Sisa ruang container adalah 1000 − 200 = 800 px, kemudian dibagi kepada B dan C dengan perbandingan `flex-grow` 1 : 2. Maka B mendapat sekitar 266,7 px dan C sekitar 533,3 px. Jika B menggunakan `flex: 1 1 auto`, ukuran awal atau flex-basis mengikuti ukuran konten terlebih dahulu sehingga pembagian ruang sisa dapat berbeda.

4. Badge menempel pada header karena elemen `.notif` tidak lagi menjadi acuan positioning. Elemen `position: absolute` mencari leluhur terdekat yang memiliki positioning, dan pada contoh ini header merupakan leluhur terdekat tersebut.

5. `sticky` tetap menjadi bagian dari aliran normal dokumen sebelum menempel di batas viewport. Sementara itu, `fixed` selalu menempel pada viewport dan keluar dari aliran normal sehingga dapat menutupi konten. Untuk navbar dashboard, saya memilih sticky karena posisi navbar tetap terlihat saat halaman digulir tanpa membuat konten awal tertutup.

6. `flex: 1` pada `.wrapper` membuat area wrapper mengambil ruang kosong yang tersedia di antara navbar dan footer. Jika aturan tersebut dihapus, wrapper hanya setinggi kontennya sehingga footer bisa naik dan tidak berada di dasar layar ketika isi halaman sedikit.

## Kesimpulan

Melalui praktikum ini, saya mempelajari cara kerja Box Model, Flexbox, dan CSS Positioning dalam mengatur tampilan halaman web. Box Model membantu mengatur ukuran elemen, Flexbox memudahkan penyusunan komponen secara rapi, sedangkan Positioning digunakan untuk mengatur letak elemen tertentu. Pada proyek dashboard, ketiga konsep tersebut diterapkan untuk membuat navbar, sidebar, kartu informasi, tabel, dan footer yang responsif. Pengujian pada ukuran desktop dan mobile perlu dilakukan kembali untuk memastikan tampilan sesuai dengan ketentuan praktikum.
