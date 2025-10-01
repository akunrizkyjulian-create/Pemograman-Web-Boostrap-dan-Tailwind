1. Jelaskan keputusan grid-cols/gap di tiap breakpoint — kenapa begitu?
-Tampilan Default (Mobile)
Konfigurasi Tailwind grid-cols-1
Wajib 1 kolom agar gambar di HP kecil terlihat besar dan jelas.
-Tampilan Tablet (md)
Konfigurasi Tailwind md:grid-cols-3
3 kolom (atau 2) memberikan feed yang ringkas dan efisien pada layar sedang.
-Tampilan Desktop (lg)
Konfigurasi Tailwind lg:grid-cols-4
Maksimal 4 kolom (atau lebih) untuk menggunakan seluruh lebar layar komputer secara efektif, membuat tampilan padat.
-Tampilan Jarak (gap)
Konfigurasi Tailwind gap-1 sm:gap-2
Digunakan jarak yang sangat kecil (1 atau 2 unit) karena feed Instagram harus memiliki jarak minimal antar gambar agar terlihat menyatu.

2.Masalah utama di mobile adalah keterbatasan ruang dan jangkauan tombol. Kita menyelesaikannya dengan utility responsif (sm:, md:):

Pengaturan Lebar Tombol:

Secara default (Mobile), tombol "Edit Profile" dibuat lebar penuh (w-full) atau lebar proporsional di dalam header agar mudah disentuh.

Pada breakpoint yang lebih besar (sm: atau md:), lebar tombol diatur kembali ke ukuran aslinya (sm:w-auto).

Penyembunyian/Pemindahan Statistik:

Statistik posts/followers disembunyikan di header desktop (hidden sm:flex) dan ditampilkan sebagai baris penuh di bawah bio (sm:hidden) untuk menghindari penumpukan di header mobile.

Rasio Gambar (aspect-square):

Menggunakan utility aspect-square (rasio 1:1) pada semua kartu postingan. Ini secara otomatis memastikan semua gambar memiliki tinggi yang konsisten di semua ukuran layar, yang merupakan masalah layout krusial di feed grid.

3. Jelaskan trade-off antara memakai banyak utility classes vs membuat komponen CSS tersendiri.
Fitur	Banyak Utility Classes (Tailwind)	Komponen CSS Tersendiri (Tradisional)
Kecepatan Awal	Sangat Cepat. Styling dilakukan langsung di HTML.	Lebih Lambat. Perlu membuat nama kelas dan switch file (HTML ke CSS).
Perawatan Kode	Mudah Dilihat/Lokal. Semua styling komponen ada di satu tempat (HTML).	Terpusat/Global. Perubahan satu kali di file CSS memengaruhi banyak komponen.
Reusabilitas	Rendah. Harus mengulang kelas di setiap elemen (kecuali pakai @apply).	Tinggi. Kelas seperti .btn-primary bisa dipakai di mana saja.
Ukuran File	Sangat Kecil (Final). Tailwind menghilangkan utility yang tidak dipakai (PurgeCSS).	Berpotensi Besar. Jika banyak CSS yang tidak terpakai, file bisa membengkak.

3.Trade-off: Utility Classes vs. Komponen CSS Tersendiri
Pendekatan 1: Banyak Utility Classes (Contoh: Tailwind CSS)
Pendekatan ini berarti Anda menumpuk banyak kelas kecil dan spesifik (seperti p-4, bg-blue-500, rounded-lg) langsung pada elemen HTML.

Keuntungan (Pro):
Kecepatan Pengembangan Cepat: Anda bisa mendesain dan mengubah tampilan elemen tanpa pernah meninggalkan file HTML. Ini sangat mempercepat prototyping dan penyesuaian kecil.

Perawatan Lokal: Styling elemen sepenuhnya terisolasi. Jika Anda mengubah kelas pada satu tombol, Anda tahu pasti bahwa perubahan itu tidak akan merusak tampilan tombol lain di halaman yang berbeda.

Kerugian (Kontra):
HTML Terlihat Penuh Sesak: Baris kode HTML bisa menjadi sangat panjang dan sulit dibaca karena dibanjiri oleh banyak kelas. Hal ini sering disebut sebagai "HTML yang kotor" atau "verbosity."

Reusabilitas Sulit: Jika Anda ingin menggunakan tampilan yang sama (misalnya, kartu berbayangan biru) di 10 tempat, Anda harus menyalin dan menempelkan semua kelas utility tersebut sebanyak 10 kali (kecuali jika Anda menggunakan fitur extractor atau @apply dari Tailwind).

Pendekatan 2: Komponen CSS Tersendiri (Contoh: BEM / CSS Tradisional)
Pendekatan ini melibatkan pembuatan kelas-kelas besar yang memiliki nama deskriptif (misalnya, .btn-primary, .card-profile-active) yang menyimpan semua properti styling di dalam file CSS terpisah.

Keuntungan (Pro):
Kode HTML Bersih: Kode HTML Anda tetap ringkas, mudah dibaca, dan semantik (misalnya, <button class="btn-primary">).

Reusabilitas Mudah: Anda hanya perlu mengubah styling di satu tempat (file CSS), dan perubahan itu akan langsung diterapkan ke semua elemen di seluruh website yang menggunakan kelas tersebut.

Kerugian (Kontra):
Pengembangan Lebih Lambat: Jika Anda hanya ingin membuat penyesuaian kecil pada satu elemen (misalnya, menambahkan margin sedikit), Anda harus beralih ke file CSS, mencari kelas yang tepat, dan menulis kode CSS baru, yang memakan waktu lebih banyak.

Risiko Efek Samping Global: Perubahan pada satu komponen CSS (misalnya .card) dapat secara tidak sengaja merusak tampilan komponen lain yang juga menggunakan atau mewarisi kelas tersebut di tempat lain (side-effects).
