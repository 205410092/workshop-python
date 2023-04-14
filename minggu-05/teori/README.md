BAB 7

7. Input and Output
Ada beberapa cara untuk mempresentasikan output dari suatu program; data dapat dicetak dalam bentuk yang dapat dibaca manusia, atau ditulis ke file untuk digunakan di masa mendatang. Bab ini akan membahas beberapa kemungkinan.

7.1. Fancier Output Formatting
Sejauh ini kita menemukan dua cara penulisan nilai: pernyataan ekspresi dan print()fungsi. (Cara ketiga menggunakan write()metode objek file; file keluaran standar dapat dirujuk sebagai sys.stdout. Lihat Referensi Perpustakaan untuk informasi lebih lanjut tentang ini.)
Seringkali Anda menginginkan kontrol lebih besar atas pemformatan keluaran Anda daripada sekadar mencetak nilai yang dipisahkan oleh ruang. Ada beberapa cara untuk memformat keluaran.

7.1.1. Formatted String Literals
Literal string terformat (disingkat juga disebut f-string) memungkinkan Anda menyertakan nilai ekspresi Python di dalam string dengan mengawali string denganforFdan menulis ekspresi sebagai {expression}.

7.1.2. The String format() Method
Jika Anda memiliki format string yang sangat panjang yang tidak ingin Anda pisahkan, alangkah baiknya jika Anda dapat mereferensikan variabel untuk diformat dengan nama, bukan dengan posisi. Ini dapat dilakukan hanya dengan meneruskan dict dan menggunakan tanda kurung siku '[]'untuk mengakses kunci.

7.1.3. Manual String Formatting
Metode str.rjust()objek string membenarkan string di bidang dengan lebar tertentu dengan melapisinya dengan spasi di sebelah kiri. Ada metode serupa str.ljust()dan str.center(). Metode ini tidak menulis apa pun, mereka hanya mengembalikan string baru. Jika string input terlalu panjang, mereka tidak memotongnya, tetapi mengembalikannya tanpa perubahan; ini akan mengacaukan tata letak kolom Anda tetapi itu biasanya lebih baik daripada alternatifnya, yang akan berbohong tentang suatu nilai. (Jika Anda benar-benar menginginkan pemotongan, Anda selalu dapat menambahkan operasi pemotongan, seperti pada x.ljust(n)[:n].)

7.1.4. Old string formatting
Operator % (modulo) juga dapat digunakan untuk pemformatan string. Diberikan , instance in diganti dengan nol atau lebih elemen . Operasi ini umumnya dikenal sebagai interpolasi string.

7.2. Reading and Writing Files
Argumen pertama adalah string yang berisi nama file. Argumen kedua adalah string lain yang berisi beberapa karakter yang menjelaskan cara penggunaan file. mode bisa 'r'saat file hanya akan dibaca, 'w' untuk ditulis saja (file yang sudah ada dengan nama yang sama akan dihapus), dan 'a'membuka file untuk ditambahkan; data apa pun yang ditulis ke file secara otomatis ditambahkan ke akhir. 'r+'membuka file untuk membaca dan menulis. Argumen mode bersifat opsional; 'r'akan dianggap jika itu dihilangkan.
Biasanya, file dibuka dalam mode teks , artinya, Anda membaca dan menulis string dari dan ke file, yang dikodekan dalam pengkodean tertentu . Jika penyandian tidak ditentukan, defaultnya tergantung platform (lihat open()). Karena UTF-8 adalah standar de-facto modern, encoding="utf-8"disarankan kecuali Anda tahu bahwa Anda perlu menggunakan penyandian yang berbeda. Menambahkan a 'b'ke mode akan membuka file dalam mode biner . Data mode biner dibaca dan ditulis sebagai bytesobjek. Anda tidak dapat menentukan penyandian saat membuka file dalam mode biner.

7.2.1. Methods of File Objects
Contoh lainnya di bagian ini akan mengasumsikan bahwa objek file yang dipanggil ftelah dibuat.
Untuk membaca isi file, panggil f.read(size), yang membaca sejumlah data dan mengembalikannya sebagai string (dalam mode teks) atau objek byte (dalam mode biner). size adalah argumen numerik opsional. Ketika ukuran dihilangkan atau negatif, seluruh konten file akan dibaca dan dikembalikan; itu masalah Anda jika file tersebut dua kali lebih besar dari memori mesin Anda. Jika tidak, sebagian besar ukuran karakter (dalam mode teks) atau ukuran byte (dalam mode biner) dibaca dan dikembalikan. Jika akhir file telah tercapai, f.read()akan mengembalikan string kosong ( '').

7.2.2. Saving structured data with json
String dapat dengan mudah ditulis dan dibaca dari file. Angka membutuhkan sedikit lebih banyak usaha, karena read()metode ini hanya mengembalikan string, yang harus diteruskan ke fungsi seperti int(), yang mengambil string seperti '123' dan mengembalikan nilai numeriknya 123. Saat Anda ingin menyimpan tipe data yang lebih kompleks seperti daftar bersarang dan kamus, parsing dan serialisasi dengan tangan menjadi rumit.
Daripada membuat pengguna terus-menerus menulis dan men-debug kode untuk menyimpan tipe data yang rumit ke file, Python memungkinkan Anda untuk menggunakan format pertukaran data populer yang disebut JSON (JavaScript Object Notation) . Modul standar yang dipanggil jsondapat mengambil hierarki data Python, dan mengubahnya menjadi representasi string; proses ini disebut serialisasi . Merekonstruksi data dari representasi string disebut deserializing . Antara serialisasi dan deserialisasi, string yang mewakili objek mungkin telah disimpan dalam file atau data, atau dikirim melalui koneksi jaringan ke beberapa mesin yang jauh.
