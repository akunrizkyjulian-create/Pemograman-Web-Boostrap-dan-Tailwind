1. Mengapa memilih konfigurasi col tertentu untuk tiap breakpoint?
-Tampilan Mobile Mobile (<576px)
Konfigurasi Boostrap col-12 (1 kolom)
untuk Di layar HP kecil, satu kolom wajib digunakan agar gambar terlihat jelas. Ini adalah desain mobile-first.
-Tampilan Tablet (≥576px)
Konfigurasi Boostrap col-sm-6 atau col-md-4 (2 atau 3 kolom)
untuk Ruang tablet cukup lebar, jadi kita bagi menjadi 2 atau 3 kolom agar feed terlihat lebih ringkas dan pengguna tidak perlu scroll terlalu jauh.
-Desktop (≥992px)
Konfigruasi Boostrap col-lg-3 (4 kolom)
untuk Layar komputer sangat lebar, jadi kita maksimalkan dengan 4 kolom (atau lebih) agar tampilan padat seperti Instagram versi web.


2.Pendekatan yang digunakan adalah menyesuaikan penempatan (layout) dan ukuran tombol menggunakan fitur utility responsif Bootstrap:

Prioritas Ukuran Penuh (Mobile): Di tampilan mobile (<576px), tombol Follow/Edit Profile (jika ada) dibuat lebar penuh (w-100 atau diletakkan dalam col-12) dan biasanya ditempatkan di bawah info bio agar mudah disentuh.

Penyembunyian Statistik (Mobile): Kita menyembunyikan statistik postingan/followers di samping tombol (d-none d-sm-flex) dan memindahkannya ke bawah bio sebagai baris terpisah untuk menghemat ruang horizontal di header.

Penyelarasan Horizontal (Desktop): Baru pada tampilan Tablet ke atas (d-sm-flex), tombol diletakkan sejajar dengan username menggunakan utility Flexbox (d-flex, align-items-center).

3. Jika postingan bertambah jadi 50, apa potensi masalah dan bagaimana solusi gridnya mengatasinya?
Potensi Masalah:
Halaman Berat & Lambat: Memuat 50 gambar sekaligus (di HTML) akan membuat halaman sangat berat, memboroskan kuota data, dan memperlambat waktu buka (load time), terutama di HP.

Guliran Panjang (Bad UX): Pengguna harus scroll sangat lama untuk mencapai bagian bawah halaman.

Solusi Grid dan Implementasi Tambahan:
Meskipun Bootstrap Grid hanya mengatur tata letak, ia menyediakan struktur yang rapi (col-lg-3, col-md-4) untuk menerapkan solusi performa:

Lazy Loading (Solusi Kinerja): Menggunakan atribut HTML loading="lazy" pada tag <img>. Ini berarti, gambar ke-20 dan seterusnya baru dimuat (di-download) saat pengguna mulai scroll mendekatinya, mengatasi masalah halaman lambat.

Infinite Scrolling (Solusi UX): Daripada menampilkan 50 gambar sekaligus, kita hanya menampilkan 12-16 gambar pertama. Grid yang dibuat (row dan col) akan memuat blok postingan tambahan secara otomatis saat pengguna mencapai bagian bawah halaman (membutuhkan JavaScript/backend), mengatasi masalah guliran panjang.
