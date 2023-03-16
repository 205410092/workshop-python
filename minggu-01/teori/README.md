BAB 1

Python adalah bahasa pemrograman serbaguna yang bisa dijalankan pada hampir semua arsitektur sistem, dan bisa digunakan untuk berbagai aplikasi di banyak bidang, mulai dari web development hingga machine learning.
Jika Anda melakukan banyak pekerjaan di komputer, akhirnya Anda menemukan bahwa ada beberapa tugas yang ingin Anda otomatisasi. Misalnya, Anda mungkin ingin melakukan pencarian-dan-ganti pada sejumlah besar file teks, atau mengganti nama dan mengatur ulang sekumpulan file foto dengan cara yang rumit. Mungkin Anda ingin menulis database kustom kecil, atau aplikasi GUI khusus, atau game sederhana.
Python mudah digunakan, tetapi ini adalah bahasa pemrograman nyata, menawarkan lebih banyak struktur dan dukungan untuk program besar daripada yang ditawarkan skrip shell atau file batch. Di sisi lain, Python juga menawarkan lebih banyak pemeriksaan kesalahan daripada C, dan, sebagai bahasa tingkat sangat tinggi , ia memiliki tipe data tingkat tinggi bawaan, seperti larik fleksibel dan kamus. Karena tipe datanya yang lebih umum, Python dapat diterapkan ke domain masalah yang jauh lebih besar daripada Awk atau bahkan Perl, namun banyak hal yang setidaknya sama mudahnya dengan Python seperti dalam bahasa-bahasa tersebut.
Python memungkinkan Anda membagi program Anda menjadi modul yang dapat digunakan kembali di program Python lainnya. Muncul dengan banyak koleksi modul standar yang dapat Anda gunakan sebagai dasar program Anda — atau sebagai contoh untuk mulai belajar memprogram dengan Python. Beberapa modul ini menyediakan hal-hal seperti I/O file, panggilan sistem, soket, dan bahkan antarmuka ke perangkat antarmuka pengguna grafis seperti Tk.
Python adalah bahasa yang ditafsirkan, yang dapat menghemat banyak waktu Anda selama pengembangan program karena tidak diperlukan kompilasi dan penautan. Penerjemah dapat digunakan secara interaktif, yang membuatnya mudah untuk bereksperimen dengan fitur bahasa, menulis program sekali pakai, atau menguji fungsi selama pengembangan program dari bawah ke atas. Ini juga merupakan kalkulator meja yang berguna.
Python memungkinkan program ditulis dengan kompak dan mudah dibaca. Program yang ditulis dengan Python biasanya jauh lebih pendek daripada program C, C++, atau Java yang setara, karena beberapa alasan:
1. Tipe data tingkat tinggi memungkinkan Anda mengekspresikan operasi kompleks dalam satu pernyataan;
2. Pengelompokan pernyataan dilakukan dengan lekukan alih-alih tanda kurung awal dan akhir;
3. Tidak diperlukan deklarasi variabel atau argumen.
BAB 2

=> Menggunakan Penerjemah Python 
- Memanggil Penerjemah
Penerjemah Python biasanya diinstal seperti /usr/local/bin/python3.11 pada mesin yang tersedia; memasukkan /usr/local/binjalur pencarian shell Unix Anda memungkinkan untuk memulainya dengan mengetikkan perintah:
ke cangkang. 1 Karena pilihan direktori tempat tinggal juru bahasa adalah opsi instalasi, tempat lain dimungkinkan; periksa dengan guru Python lokal atau administrator sistem Anda. (Misalnya, /usr/local/pythonadalah lokasi alternatif yang populer.)

Pada mesin Windows tempat Anda menginstal Python dari Microsoft Store , python3.11perintah akan tersedia. Jika Anda menginstal peluncur py.exe , Anda dapat menggunakan py perintah. Lihat Excursus: Mengatur variabel lingkungan untuk cara lain meluncurkan Python.

Mengetik karakter akhir file ( di Unix, di Windows) pada prompt utama menyebabkan juru bahasa keluar dengan status keluar nol. Jika tidak berhasil, Anda dapat keluar dari penerjemah dengan mengetikkan perintah berikut: .Control-DControl-Zquit()
Cara kedua untuk memulai juru bahasa adalah , yang mengeksekusi pernyataan dalam command , analog dengan opsi shell . Karena pernyataan Python sering mengandung spasi atau karakter lain yang khusus untuk shell, biasanya disarankan untuk mengutip perintah secara keseluruhan.python -c command [arg] ...-c

Beberapa modul Python juga berguna sebagai skrip. Ini dapat dipanggil menggunakan , yang mengeksekusi file sumber untuk modul seolah-olah Anda telah menyebutkan nama lengkapnya di baris perintah.python -m module [arg] ...

Saat file skrip digunakan, terkadang berguna untuk dapat menjalankan skrip dan masuk ke mode interaktif sesudahnya. Ini dapat dilakukan dengan melewati -i sebelum skrip.

Semua opsi baris perintah dijelaskan di Baris perintah dan lingkungan .
- Melewati Argumen 
Saat diketahui oleh juru bahasa, nama skrip dan argumen tambahan selanjutnya diubah menjadi daftar string dan ditetapkan ke variabel argv dalam sysmodul. Anda dapat mengakses daftar ini dengan menjalankan . Panjang daftar setidaknya satu; ketika tidak ada skrip dan tidak ada argumen yang diberikan, adalah string kosong. Ketika nama skrip diberikan sebagai (artinya input standar), disetel ke . Ketika perintah digunakan, diatur ke . Saat modul digunakan, atur ke nama lengkap modul yang terletak. Opsi yang ditemukan setelah perintah atau modul tidak dikonsumsi oleh pemrosesan opsi juru bahasa Python tetapi dibiarkanimport syssys.argv[0]'-'sys.argv[0]'-'-c sys.argv[0]'-c'-m sys.argv[0]-c -m sys.argvuntuk menangani perintah atau modul.
- Modus Interaktif 
Ketika perintah dibaca dari tty, interpreter dikatakan dalam mode interaktif . Dalam mode ini ia meminta perintah berikutnya dengan prompt utama , biasanya tiga tanda lebih besar dari ( >>>); untuk baris lanjutan diminta dengan prompt sekunder , secara default tiga titik ( ...).
Penerjemah dan Lingkungannya 
- Pengkodean Kode Sumber
Secara default, file sumber Python diperlakukan sebagai dikodekan dalam UTF-8. Dalam pengkodean itu, karakter dari sebagian besar bahasa di dunia dapat digunakan secara bersamaan dalam literal string, pengidentifikasi, dan komentar — meskipun perpustakaan standar hanya menggunakan karakter ASCII untuk pengidentifikasi, sebuah konvensi yang harus diikuti oleh kode portabel apa pun. Untuk menampilkan semua karakter ini dengan benar, editor Anda harus mengenali bahwa file tersebut adalah UTF-8, dan harus menggunakan font yang mendukung semua karakter dalam file.
