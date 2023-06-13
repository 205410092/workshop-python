BAB 10

10. Brief Tour of the Standard Library

10.1. Operating System Interface

Modul ini osmenyediakan lusinan fungsi untuk berinteraksi dengan sistem operasi,Pastikan untuk menggunakan gaya alih-alih . Ini akan mencegah membayangi fungsi bawaan yang beroperasi jauh berbeda

10.3. Command Line Arguments

Skrip utilitas umum seringkali perlu memproses argumen baris perintah. Argumen ini disimpan dalam atribut sysmodul argv sebagai daftar. 

10.5. String Pattern Matching

Modul ini remenyediakan alat ekspresi reguler untuk pemrosesan string tingkat lanjut. Untuk pencocokan dan manipulasi yang rumit, ekspresi reguler menawarkan solusi ringkas dan optimal.

10.6. Mathematics

Modul ini mathmemberikan akses ke fungsi library C yang mendasari matematika floating point.

10.7. Internet Access

Ada sejumlah modul untuk mengakses internet dan memproses protokol internet. Dua yang paling sederhana adalah urllib.requestuntuk mengambil data dari URL dan smtplibuntuk mengirim email.

10.8. Dates and Times

Modul datetimemenyediakan kelas untuk memanipulasi tanggal dan waktu dengan cara sederhana dan kompleks. Sementara aritmatika tanggal dan waktu didukung, fokus penerapannya adalah pada ekstraksi anggota yang efisien untuk pemformatan dan manipulasi keluaran. Modul ini juga mendukung objek yang sadar zona waktu.

10.9. Data Compression

Pengarsipan data umum dan format kompresi didukung langsung oleh modul termasuk: zlib, gzip, bz2, lzma, zipfiledan tarfile.

10.10. Performance Measurement

Beberapa pengguna Python mengembangkan minat yang mendalam untuk mengetahui kinerja relatif dari berbagai pendekatan untuk masalah yang sama. Python menyediakan alat pengukuran yang segera menjawab pertanyaan tersebut.
Misalnya, mungkin tergoda untuk menggunakan fitur packing dan unpacking tuple daripada pendekatan tradisional untuk bertukar argumen.

10.11. Quality Control

Salah satu pendekatan untuk mengembangkan perangkat lunak berkualitas tinggi adalah dengan menulis tes untuk setiap fungsi saat dikembangkan dan sering menjalankan tes tersebut selama proses pengembangan.
Modul ini doctestmenyediakan alat untuk memindai modul dan memvalidasi pengujian yang disematkan dalam dokumen program. Konstruksi pengujian semudah memotong-dan-menempelkan panggilan biasa beserta hasilnya ke dalam docstring.

BAB 11

11. Brief Tour of the Standard Library — Part II

Tur kedua ini mencakup modul lanjutan yang mendukung kebutuhan pemrograman profesional. Modul ini jarang muncul dalam skrip kecil.

11.1. Output Formattin

Modul ini pprintmenawarkan kontrol yang lebih canggih atas pencetakan objek bawaan dan yang ditentukan pengguna dengan cara yang dapat dibaca oleh juru bahasa. Ketika hasilnya lebih panjang dari satu baris, "printer cantik" menambahkan jeda baris dan lekukan untuk mengungkapkan struktur data dengan lebih jelas.

11.2. Templating

Modul stringmencakup kelas serbaguna Templatedengan sintaks yang disederhanakan yang cocok untuk diedit oleh pengguna akhir. Ini memungkinkan pengguna untuk menyesuaikan aplikasi mereka tanpa harus mengubah aplikasi.
Formatnya menggunakan nama placeholder yang dibentuk oleh $dengan pengidentifikasi Python yang valid (karakter alfanumerik dan garis bawah).

11.3. Working with Binary Data Record Layouts

Modul structmenyediakan pack()dan unpack()fungsi untuk bekerja dengan format catatan biner panjang variabel. Contoh berikut menunjukkan cara mengulang informasi header dalam file ZIP tanpa menggunakan zipfilemodul. Kemas kode "H"dan "I"masing-masing mewakili dua dan empat byte angka yang tidak ditandatangani.

11.4. Multi-threading

Threading adalah teknik untuk memisahkan tugas yang tidak bergantung secara berurutan. Utas dapat digunakan untuk meningkatkan daya tanggap aplikasi yang menerima input pengguna saat tugas lain berjalan di latar belakang. Kasus penggunaan terkait sedang menjalankan I/O secara paralel dengan perhitungan di utas lainnya.

11.5. Logging

Modul ini loggingmenawarkan sistem logging berfitur lengkap dan fleksibel. Sederhananya, pesan log dikirim ke file atau ke sys.stderr:
Secara default, pesan informasi dan debug disembunyikan dan output dikirim ke kesalahan standar. Opsi keluaran lainnya termasuk merutekan pesan melalui email, datagram, soket, atau ke Server HTTP. Filter baru dapat memilih perutean yang berbeda berdasarkan prioritas pesan: DEBUG, INFO, WARNING, ERROR, dan CRITICAL.
Sistem logging dapat dikonfigurasi langsung dari Python atau dapat dimuat dari file konfigurasi yang dapat diedit pengguna untuk logging yang disesuaikan tanpa mengubah aplikasi.

11.6. Weak References

Python melakukan manajemen memori otomatis (penghitungan referensi untuk sebagian besar objek dan pengumpulan sampah untuk menghilangkan siklus). Memori dibebaskan segera setelah referensi terakhir untuk itu telah dihilangkan.
Pendekatan ini berfungsi dengan baik untuk sebagian besar aplikasi, tetapi kadang-kadang ada kebutuhan untuk melacak objek hanya selama mereka digunakan oleh sesuatu yang lain. Sayangnya, hanya melacaknya akan membuat referensi yang menjadikannya permanen. Modul ini weakrefmenyediakan alat untuk melacak objek tanpa membuat referensi. Ketika objek tidak lagi diperlukan, secara otomatis dihapus dari tabel ref lemah dan panggilan balik dipicu untuk objek ref lemah.

11.7. Tools for Working with Lists

Banyak kebutuhan struktur data dapat dipenuhi dengan tipe daftar bawaan. Namun, terkadang ada kebutuhan untuk penerapan alternatif dengan pertukaran kinerja yang berbeda.

11.8. Decimal Floating Point Arithmetic

Modul ini decimalmenawarkan Decimaltipe data untuk aritmatika floating point desimal. Dibandingkan dengan implementasi built-in float dari floating point biner, kelas ini sangat membantu
Misalnya, menghitung pajak 5% untuk biaya telepon 70 sen memberikan hasil yang berbeda dalam floating point desimal dan floating point biner.
