BAB 12

12. Virtual Environments and Packages

12.1. Introduction

Aplikasi Python akan sering menggunakan paket dan modul yang tidak disertakan sebagai bagian dari pustaka standar. Aplikasi kadang-kadang membutuhkan versi perpustakaan tertentu, karena aplikasi mungkin memerlukan bug tertentu yang telah diperbaiki atau aplikasi mungkin ditulis menggunakan versi lama dari antarmuka perpustakaan.
Ini berarti tidak mungkin satu instalasi Python memenuhi persyaratan setiap aplikasi. Jika aplikasi A membutuhkan versi 1.0 dari modul tertentu tetapi aplikasi B membutuhkan versi 2.0, maka persyaratan tersebut bertentangan dan menginstal versi 1.0 atau 2.0 akan membuat satu aplikasi tidak dapat dijalankan.
Solusi untuk masalah ini adalah membuat lingkungan virtual , pohon direktori mandiri yang berisi instalasi Python untuk versi Python tertentu, ditambah sejumlah paket tambahan.
Aplikasi yang berbeda kemudian dapat menggunakan lingkungan virtual yang berbeda. Untuk mengatasi contoh konflik persyaratan sebelumnya, aplikasi A dapat memiliki lingkungan virtualnya sendiri dengan versi 1.0 diinstal sementara aplikasi B memiliki lingkungan virtual lain dengan versi 2.0. Jika aplikasi B memerlukan pustaka yang ditingkatkan ke versi 3.0, ini tidak akan memengaruhi lingkungan aplikasi A.

12.2. Creating Virtual Environments

Modul yang digunakan untuk membuat dan mengelola lingkungan virtual disebut venv. venvbiasanya akan menginstal versi Python terbaru yang Anda miliki. Jika Anda memiliki beberapa versi Python di sistem Anda, Anda dapat memilih versi Python tertentu dengan menjalankan python3atau versi apa pun yang Anda inginkan.
Untuk membuat lingkungan virtual, tentukan direktori tempat Anda ingin meletakkannya, dan jalankan modul venvsebagai skrip dengan jalur direktori:
python -m venv tutorial-env
Ini akan membuat tutorial-envdirektori jika tidak ada, dan juga membuat direktori di dalamnya yang berisi salinan juru bahasa Python dan berbagai file pendukung.
Lokasi direktori umum untuk lingkungan virtual adalah .venv. Nama ini membuat direktori biasanya tersembunyi di shell Anda dan dengan demikian menyingkir sambil memberinya nama yang menjelaskan mengapa direktori itu ada. Ini juga mencegah bentrok dengan .envfile definisi variabel lingkungan yang didukung beberapa perkakas

12.3. Managing Packages with pip

Anda dapat menginstal, memutakhirkan, dan menghapus paket menggunakan program bernama pip . Secara default pipakan menginstal paket dari Python Package Index . Anda dapat menelusuri Indeks Paket Python dengan membukanya di browser web Anda.
pipmemiliki sejumlah subperintah: "install", "uninstall", "freeze", dll. (Lihat panduan Memasang Modul Python untuk dokumentasi lengkap untuk pip.)
Jika Anda menjalankan kembali perintah ini, pipakan melihat bahwa versi yang diminta telah diinstal dan tidak melakukan apa pun. Anda dapat memberikan nomor versi yang berbeda untuk mendapatkan versi tersebut, atau Anda dapat menjalankan untuk memutakhirkan paket ke versi terbaru:python -m pip install --upgrade

