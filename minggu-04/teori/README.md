BAB 6

6. Modules

Jika Anda keluar dari juru bahasa Python dan memasukkannya lagi, definisi yang Anda buat (fungsi dan variabel) akan hilang. Oleh karena itu, jika Anda ingin menulis program yang agak panjang, lebih baik Anda menggunakan editor teks untuk menyiapkan input untuk juru bahasa dan menjalankannya dengan file tersebut sebagai input. Ini dikenal sebagai membuat skrip . Saat program Anda semakin panjang, Anda mungkin ingin membaginya menjadi beberapa file untuk pemeliharaan yang lebih mudah. Anda mungkin juga ingin menggunakan fungsi praktis yang telah Anda tulis di beberapa program tanpa menyalin definisinya ke setiap program.
Untuk mendukung ini, Python memiliki cara untuk meletakkan definisi dalam file dan menggunakannya dalam skrip atau dalam contoh interaktif dari juru bahasa. File seperti itu disebut modul ; definisi dari modul dapat diimpor ke modul lain atau ke modul utama (kumpulan variabel yang dapat Anda akses dalam skrip yang dijalankan di tingkat atas dan dalam mode kalkulator).

6.1. More on Modules

Modul dapat berisi pernyataan yang dapat dieksekusi serta definisi fungsi. Pernyataan ini dimaksudkan untuk menginisialisasi modul. Mereka dieksekusi hanya saat pertama kali nama modul ditemukan dalam pernyataan impor. 1 (Mereka juga dijalankan jika file dijalankan sebagai skrip.)
Setiap modul memiliki ruang nama pribadinya sendiri, yang digunakan sebagai ruang nama global oleh semua fungsi yang ditentukan dalam modul. Dengan demikian, pembuat modul dapat menggunakan variabel global di dalam modul tanpa khawatir tentang bentrok yang tidak disengaja dengan variabel global pengguna. Di sisi lain, jika Anda tahu apa yang Anda lakukan, Anda dapat menyentuh variabel global modul dengan notasi yang sama yang digunakan untuk merujuk ke fungsinya, modname.itemname.

6.1.1. Executing modules as scripts

Saat Anda menjalankan modul Python dengan
python fibo.py <arguments>
kode dalam modul akan dieksekusi, sama seperti jika Anda mengimpornya, tetapi dengan set __name__ke "__main__".

6.1.2. The Module Search Path
  
Saat nama modul spamdiimpor, interpreter pertama-tama akan mencari modul bawaan dengan nama tersebut. Nama modul ini tercantum dalam sys.builtin_module_names. Jika tidak ditemukan, ia akan mencari file bernama spam.pydalam daftar direktori yang diberikan oleh variabel sys.path. sys.pathdiinisialisasi dari lokasi berikut:
- Direktori yang berisi skrip input (atau direktori saat ini ketika tidak ada file yang ditentukan).
- PYTHONPATH(daftar nama direktori, dengan sintaks yang sama dengan variabel shellPATH).
- Default yang bergantung pada penginstalan (berdasarkan konvensi termasuk site-packagesdirektori, ditangani oleh sitemodul).

6.1.3. “Compiled” Python file
  
Untuk mempercepat pemuatan modul, Python meng-cache versi terkompilasi dari setiap modul di __pycache__direktori dengan nama , di mana versi mengkodekan format file yang dikompilasi; umumnya berisi nomor versi Python. Misalnya, dalam rilis CPython 3.3, versi spam.py yang dikompilasi akan di-cache sebagai . Konvensi penamaan ini memungkinkan modul yang dikompilasi dari rilis yang berbeda dan versi Python yang berbeda untuk hidup berdampingan.

6.2. Standard Modules
  
Python hadir dengan pustaka modul standar, dijelaskan dalam dokumen terpisah, Referensi Pustaka Python (“Referensi Pustaka” selanjutnya). Beberapa modul dibangun ke dalam juru bahasa; ini memberikan akses ke operasi yang bukan bagian dari inti bahasa tetapi tetap dibangun, baik untuk efisiensi atau untuk menyediakan akses ke primitif sistem operasi seperti panggilan sistem. Kumpulan modul tersebut adalah opsi konfigurasi yang juga bergantung pada platform yang mendasarinya. Misalnya, winregmodul hanya tersedia di sistem Windows.

6.3. The dir() Function
  
Fungsi bawaan dir()digunakan untuk mencari tahu nama mana yang didefinisikan oleh modul. 

6.4. Packages
  
Paket adalah cara menyusun ruang nama modul Python dengan menggunakan "nama modul bertitik". Misalnya, nama modul A.Bmenunjukkan submodule yang dinamai Bdalam paket bernama A. Sama seperti penggunaan modul menyelamatkan pembuat modul yang berbeda dari harus khawatir tentang nama variabel global satu sama lain, penggunaan nama modul bertitik menyelamatkan penulis paket multi-modul seperti NumPy atau Pillow dari harus khawatir tentang nama modul satu sama lain.
Misalkan Anda ingin merancang kumpulan modul ("paket") untuk penanganan file suara dan data suara yang seragam. Ada banyak format file suara yang berbeda (biasanya dikenali dari ekstensinya, misalnya: .wav, .aiff, .au), jadi Anda mungkin perlu membuat dan memelihara koleksi modul yang terus bertambah untuk konversi antara berbagai format file. Ada juga banyak operasi berbeda yang mungkin ingin Anda lakukan pada data suara (seperti mencampur, menambahkan gema, menerapkan fungsi equalizer, membuat efek stereo buatan), jadi selain itu Anda akan menulis aliran modul tanpa henti untuk dilakukan.

6.4.1. Importing * From a Package
  
Sekarang apa yang terjadi ketika pengguna menulis ? Idealnya, orang akan berharap bahwa ini entah bagaimana keluar ke sistem file, menemukan submodul mana yang ada dalam paket, dan mengimpor semuanya. Ini bisa memakan waktu lama dan mengimpor sub-modul mungkin memiliki efek samping yang tidak diinginkan yang seharusnya hanya terjadi ketika sub-modul diimpor secara eksplisit.Satu-satunya solusi adalah pembuat paket menyediakan indeks eksplisit dari paket tersebut.

6.4.2. Intra-package References
  
Ketika paket disusun menjadi sub-paket (seperti paket sounddalam contoh), Anda dapat menggunakan absolute imports untuk merujuk ke submodul dari paket saudara. Misalnya, jika modul sound.filters.vocoderperlu menggunakan echomodul dalam sound.effectspaket, dapat menggunakan.

6.4.3. Packages in Multiple Directories
  
Paket mendukung satu lagi atribut khusus, __path__. Ini diinisialisasi menjadi daftar yang berisi nama direktori yang menyimpan paket __init__.pysebelum kode dalam file tersebut dijalankan. Variabel ini dapat dimodifikasi; hal itu memengaruhi pencarian modul dan subpaket di masa mendatang yang terdapat dalam paket.
Meskipun fitur ini tidak sering dibutuhkan, fitur ini dapat digunakan untuk memperluas kumpulan modul yang ditemukan dalam sebuah paket.
