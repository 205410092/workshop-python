Project Layout

Buat direktori proyek

Kemudian ikuti petunjuk penginstalan untuk menyiapkan lingkungan virtual Python dan instal Flask untuk proyek Anda.

Tutorial akan menganggap Anda bekerja dari flask-tutorial direktori mulai sekarang. Nama file di bagian atas setiap blok kode relatif terhadap direktori ini.

Namun, saat proyek semakin besar, menyimpan semua kode dalam satu file menjadi hal yang luar biasa. Proyek Python menggunakan paket untuk mengatur kode menjadi beberapa modul yang dapat diimpor jika diperlukan, dan tutorial juga akan melakukannya.

Application Setup

Aplikasi Flask adalah turunan dari kelas Flask. Segala sesuatu tentang aplikasi, seperti konfigurasi dan URL, akan didaftarkan ke kelas ini.

Cara paling mudah untuk membuat aplikasi Flask adalah dengan membuat Flaskinstance global langsung di bagian atas kode Anda, seperti cara "Hello, World!" contoh lakukan pada halaman sebelumnya. Meskipun ini sederhana dan berguna dalam beberapa kasus, ini dapat menyebabkan beberapa masalah rumit saat proyek berkembang.

The Application Factory

Saatnya memulai pengkodean! Buat flaskrdirektori dan tambahkan __init__.pyfile. Tugas __init__.pyganda: itu akan berisi pabrik aplikasi, dan itu memberi tahu Python bahwa direktori flaskr harus diperlakukan sebagai sebuah paket.

Define and Access the Database

Aplikasi akan menggunakan database SQLite untuk menyimpan pengguna dan postingan. Python hadir dengan dukungan bawaan untuk SQLite dalam sqlite3 modul.

SQLite nyaman karena tidak memerlukan pengaturan server database terpisah dan sudah ada di dalam Python. Namun, jika permintaan bersamaan mencoba untuk menulis ke database pada saat yang sama, permintaan tersebut akan melambat karena setiap penulisan terjadi secara berurutan. Aplikasi kecil tidak akan memperhatikan ini. Setelah Anda menjadi besar, Anda mungkin ingin beralih ke database lain.

Connect to the Database

Hal pertama yang harus dilakukan saat bekerja dengan database SQLite (dan sebagian besar pustaka database Python lainnya) adalah membuat koneksi ke sana. Permintaan dan operasi apa pun dilakukan menggunakan koneksi, yang ditutup setelah pekerjaan selesai.

Dalam aplikasi web, koneksi ini biasanya terkait dengan permintaan. Itu dibuat di beberapa titik saat menangani permintaan, dan ditutup sebelum respons dikirim.

Create the Tables

Di SQLite, data disimpan dalam tabel dan kolom . Ini perlu dibuat sebelum Anda dapat menyimpan dan mengambil data. Flaskr akan menyimpan pengguna di usertabel, dan posting di posttabel. Buat file dengan perintah SQL yang diperlukan untuk membuat tabel kosong.

Register with the Application

Fungsi close_dbdan init_db_commandharus didaftarkan dengan instance aplikasi; jika tidak, mereka tidak akan digunakan oleh aplikasi. Namun, karena Anda menggunakan fungsi pabrik, instans tersebut tidak tersedia saat menulis fungsi. Alih-alih, tulis fungsi yang mengambil aplikasi dan melakukan pendaftaran.

Initialize the Database File

Sekarang setelah init-dbterdaftar dengan aplikasi, itu bisa dipanggil menggunakan flaskperintah, mirip dengan runperintah dari halaman sebelumnya.

Blueprints and Views

Anda akan menggunakan teknik yang sama dengan yang Anda pelajari saat menulis cetak biru autentikasi untuk menulis cetak biru blog. Blog harus mencantumkan semua posting, mengizinkan pengguna yang masuk untuk membuat posting, dan mengizinkan penulis posting untuk mengedit atau menghapusnya.

The Blueprint

Tentukan cetak biru dan daftarkan di pabrik aplikasi.

Index

Indeks akan menampilkan semua posting, paling baru terlebih dahulu. A JOINdigunakan agar informasi penulis dari usertabel tersedia di hasil.

Create

Tampilan createberfungsi sama dengan registertampilan autentikasi. Entah formulir ditampilkan, atau data yang diposting divalidasi dan posting ditambahkan ke database atau kesalahan ditampilkan.

Dekorator login_requiredyang Anda tulis sebelumnya digunakan pada tampilan blog. Seorang pengguna harus masuk untuk mengunjungi tampilan ini, jika tidak mereka akan dialihkan ke halaman masuk.

Update

Baik tampilan updatedan deleteperlu diambil post oleh iddan memeriksa apakah penulis cocok dengan pengguna yang masuk. Untuk menghindari duplikasi kode, Anda dapat menulis fungsi untuk mendapatkan postdan memanggilnya dari setiap tampilan.

Delete

Tampilan hapus tidak memiliki templatnya sendiri, tombol hapus adalah bagian dari update.htmldan memposting ke /<id>/deleteURL. Karena tidak ada template, itu hanya akan menangani POSTmetode dan kemudian mengarahkan ke indextampilan.
