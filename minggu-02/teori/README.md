BAB 4

4.More Control Flow Tools

Selain whilepernyataan yang baru saja diperkenalkan, Python menggunakan pernyataan kontrol aliran biasa yang dikenal dari bahasa lain, dengan beberapa perubahan.

4.1. if Statements

Mungkin jenis pernyataan yang paling terkenal adalah ifpernyataan.Bisa ada nol atau lebih elifbagian, dan elsebagian itu opsional. Kata kunci ' elif' adalah kependekan dari 'else if', dan berguna untuk menghindari indentasi yang berlebihan. Sebuah if… elif… elif… urutan adalah pengganti switchatau casepernyataan yang ditemukan dalam bahasa lain.Jika Anda membandingkan nilai yang sama dengan beberapa konstanta, atau memeriksa tipe atau atribut tertentu,Anda mungkin juga menganggap matchpernyataan itu berguna. Untuk detail lebih lanjut lihat Pernyataa kecocokan.

4.2. for Statements

Pernyataan fordalam Python sedikit berbeda dari yang biasa Anda gunakan di C atau Pascal. Daripada selalu mengulangi perkembangan aritmatika angka (seperti di Pascal), atau memberi pengguna kemampuan untuk menentukan langkah iterasi dan menghentikan kondisi (sebagai C), pernyataan Python mengulangi item dari urutan apa pun (daftar atau fora string), dalam urutan yang muncul dalam urutan. Misalnya (tidak ada permainan kata-kata)

4.3. The range() Function

Titik akhir yang diberikan tidak pernah menjadi bagian dari urutan yang dihasilkan; range(10)menghasilkan 10 nilai, indeks legal untuk item dengan urutan panjang 10. Dimungkinkan untuk membiarkan rentang dimulai dari angka lain, atau menentukan kenaikan yang berbeda (bahkan negatif; terkadang ini disebut 'langkah').Dalam banyak hal objek yang dikembalikan oleh range()berperilaku seolah-olah itu adalah daftar, tetapi sebenarnya bukan. Ini adalah objek yang mengembalikan item berturut-turut dari urutan yang diinginkan saat Anda mengulanginya, tetapi tidak benar-benar membuat daftar, sehingga menghemat ruang.

4.4. break and continue Statements, and else Clauses on Loops

Pernyataan break, seperti di C, keluar dari penutup foratau whileloop terdalam.
Pernyataan pengulangan mungkin memiliki elseklausa; itu dieksekusi ketika loop berakhir melalui kelelahan iterable (dengan for) atau ketika kondisi menjadi salah (dengan while), tetapi tidak ketika loop diakhiri dengan breakpernyataan. Ini dicontohkan oleh loop berikut, yang mencari bilangan prima.Saat digunakan dengan perulangan, elseklausa memiliki lebih banyak kesamaan dengan elseklausa pernyataan trydaripada pernyataan if: klausa trypernyataan elseberjalan saat tidak ada pengecualian yang terjadi, dan klausa perulangan elseberjalan saat tidak break terjadi. Untuk informasi lebih lanjut tentang trypernyataan dan pengecualian, lihat Menangani Pengecualian.

4.6. match Statements

Pernyataan matchmengambil ekspresi dan membandingkan nilainya dengan pola berurutan yang diberikan sebagai satu atau lebih blok kasus. Ini mirip dengan pernyataan switch di C, Java atau JavaScript (dan banyak bahasa lainnya) tetapi lebih mirip dengan pencocokan pola dalam bahasa seperti Rust atau Haskell. Hanya pola pertama yang cocok yang akan dieksekusi dan juga dapat mengekstrak komponen (elemen urutan atau atribut objek) dari nilai menjadi variabel.

4.7. Defining Functions

Kata kunci memperkenalkan definisidef fungsi . Itu harus diikuti oleh nama fungsi dan daftar parameter formal yang dikurung. Pernyataan yang membentuk isi fungsi dimulai dari baris berikutnya, dan harus diberi indentasi.
Pernyataan pertama dari badan fungsi secara opsional dapat berupa string literal; literal string ini adalah string dokumentasi fungsi, atau docstring . (Selengkapnya tentang docstring dapat ditemukan di bagian Documentation Strings .) Ada alat yang menggunakan docstring untuk menghasilkan dokumentasi online atau cetak secara otomatis, atau untuk membiarkan pengguna menelusuri kode secara interaktif; merupakan praktik yang baik untuk menyertakan dokumen dalam kode yang Anda tulis, jadi biasakanlah.
Eksekusi suatu fungsi memperkenalkan tabel simbol baru yang digunakan untuk variabel lokal dari fungsi tersebut. Lebih tepatnya, semua penugasan variabel dalam suatu fungsi menyimpan nilai dalam tabel simbol lokal; sedangkan referensi variabel pertama-tama terlihat di tabel simbol lokal, lalu di tabel simbol lokal fungsi terlampir, lalu di tabel simbol global, dan terakhir di tabel nama bawaan. Dengan demikian, variabel global dan variabel fungsi terlampir tidak dapat secara langsung diberi nilai dalam suatu fungsi (kecuali, untuk variabel global, disebutkan dalam pernyataan global, atau, untuk variabel fungsi terlampir, disebutkan dalam nonlocalpernyataan), meskipun mereka dapat direferensikan.
Parameter aktual (argumen) untuk pemanggilan fungsi diperkenalkan di tabel simbol lokal dari fungsi yang dipanggil saat dipanggil; dengan demikian, argumen diteruskan menggunakan call by value (di mana nilainya selalu merupakan referensi objek , bukan nilai objek). 1 Ketika suatu fungsi memanggil fungsi lain, atau memanggil dirinya sendiri secara rekursif, tabel simbol lokal baru dibuat untuk panggilan itu.Definisi fungsi mengaitkan nama fungsi dengan objek fungsi dalam tabel simbol saat ini. Penerjemah mengenali objek yang ditunjuk oleh nama itu sebagai fungsi yang ditentukan pengguna. Nama lain juga dapat menunjuk ke objek fungsi yang sama dan juga dapat digunakan untuk mengakses fungsi tersebut.Dimungkinkan juga untuk mendefinisikan fungsi dengan sejumlah variabel argumen. Ada tiga bentuk yang bisa digabungkan.

4.8.1. Default Argument Values

Bentuk yang paling berguna adalah menentukan nilai default untuk satu atau beberapa argumen. Ini menciptakan fungsi yang dapat dipanggil dengan lebih sedikit argumen daripada yang diizinkan.
Fungsi ini dapat dipanggil dengan beberapa cara:
- hanya memberikan argumen wajib: ask_ok('Do you really want to quit?')
- memberikan salah satu argumen opsional: ask_ok('OK to overwrite the file?', 2)
- atau bahkan memberikan semua argumen: ask_ok('OK to overwrite the file?', 2, 'Come on, only yes or no!')
Contoh ini juga memperkenalkan inkata kunci. Ini menguji apakah urutan berisi nilai tertentu atau tidak.

4.8.3. Special parameters

Secara default, argumen dapat diteruskan ke fungsi Python baik dengan posisi atau secara eksplisit dengan kata kunci. Untuk keterbacaan dan kinerja, masuk akal untuk membatasi cara argumen dapat diteruskan sehingga pengembang hanya perlu melihat definisi fungsi untuk menentukan apakah item diteruskan oleh posisi, posisi atau kata kunci, atau kata kunci.dimana /dan *adalah opsional. Jika digunakan, simbol ini menunjukkan jenis parameter dengan cara argumen 
dapat diteruskan ke fungsi: hanya posisi, posisi atau kata kunci, dan kata kunci saja. Parameter kata kunci juga disebut sebagai parameter bernama.

4.8.3.1. Positional-or-Keyword Arguments

Jika /dan *tidak ada dalam definisi fungsi, argumen dapat diteruskan ke fungsi berdasarkan posisi atau kata kunci.

4.8.3.2. Positional-Only Parameters

Melihat ini sedikit lebih detail, dimungkinkan untuk menandai parameter tertentu sebagai positional-only. Jika positional-only , urutan parameter penting, dan parameter tidak dapat diteruskan dengan kata kunci.Parameter khusus posisi ditempatkan sebelum /(garis miring). The /digunakan untuk secara logis memisahkan parameter hanya posisional dari parameter lainnya. Jika tidak ada /dalam definisi fungsi, tidak ada parameter hanya posisi Parameter yang mengikuti /mungkin berupa posisi-atau-kata kunci atau kata kunci saja.

4.8.3.3. Keyword-Only Arguments

Untuk menandai parameter sebagai hanya kata kunci , yang menunjukkan bahwa parameter harus diteruskan oleh argumen kata kunci, tempatkan an *di daftar argumen tepat sebelum parameter khusus kata kunci pertama.

4.8.3.5. Recap

Kasus penggunaan akan menentukan parameter mana yang akan digunakan dalam definisi fungsi:

def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):
Sebagai panduan:
- Gunakan hanya posisi jika Anda ingin nama parameter tidak tersedia untuk pengguna.Ini berguna ketika nama parameter tidak memiliki arti sebenarnya, jika Anda ingin menerapkan urutan argumen saat fungsi dipanggil atau jika Anda perlu mengambil beberapa parameter posisi dan kata kunci arbitrer.
- Gunakan hanya kata kunci jika nama memiliki arti dan definisi fungsi lebih mudah dipahami dengan nama yang eksplisit atau Anda ingin mencegah pengguna mengandalkan posisi argumen yang diteruskan.
- Untuk API, gunakan positional-only untuk mencegah perubahan API yang rusak jika nama parameter diubah di masa mendatang.

4.8.4. Arbitrary Argument Lists

Terakhir, opsi yang paling jarang digunakan adalah menentukan bahwa suatu fungsi dapat dipanggil dengan jumlah argumen yang berubah-ubah. Argumen ini akan dibungkus dalam sebuah tuple (lihat Tuples and Sequences ).Sebelum jumlah argumen variabel, nol atau lebih argumen normal dapat terjadi.

def write_multiple_items(file, separator, *args):
    file.write(separator.join(args))

Biasanya, argumen variadik ini akan menjadi yang terakhir dalam daftar parameter formal, karena mereka meraup semua argumen masukan yang tersisa yang diteruskan ke fungsi. Parameter formal apa pun yang muncul setelah *args parameter adalah argumen 'kata kunci saja', yang berarti bahwa parameter tersebut hanya dapat digunakan sebagai kata kunci daripada argumen posisional.

4.8.5. Unpacking Argument Lists

Situasi sebaliknya terjadi ketika argumen sudah ada dalam daftar atau tupel tetapi perlu dibongkar untuk pemanggilan fungsi yang memerlukan argumen posisi terpisah. Misalnya, fungsi bawaan range()mengharapkan argumen start dan stop yang terpisah. Jika tidak tersedia secara terpisah, tulis pemanggilan fungsi dengan operator *untuk membongkar argumen dari daftar atau tupel.

4.8.6. Lambda Expressions

Fungsi anonim kecil dapat dibuat dengan lambdakata kunci. Fungsi ini mengembalikan jumlah dari dua argumennya: . Fungsi Lambda dapat digunakan di mana pun objek fungsi diperlukan. Mereka secara sintaksis dibatasi untuk satu ekspresi. Secara semantik, mereka hanyalah gula sintaksis untuk definisi fungsi normal. Seperti definisi fungsi bersarang, fungsi lambda dapat mereferensikan variabel dari cakupan yang memuat:lambda a, b: a+b.

4.8.7. Documentation Strings

Berikut adalah beberapa konvensi tentang konten dan pemformatan string dokumentasi.Baris pertama harus selalu merupakan ringkasan singkat dan ringkas dari tujuan objek. Untuk singkatnya, itu tidak boleh secara eksplisit menyatakan nama atau tipe objek, karena ini tersedia dengan cara lain (kecuali jika nama tersebut kebetulan merupakan kata kerja yang menjelaskan operasi fungsi). Baris ini harus dimulai dengan huruf kapital dan diakhiri dengan titik.

Jika ada lebih banyak baris dalam string dokumentasi, baris kedua harus kosong, memisahkan ringkasan secara visual dari deskripsi lainnya. Baris berikut harus berupa satu atau lebih paragraf yang menjelaskan konvensi pemanggilan objek, efek sampingnya, dll.

Parser Python tidak menghapus indentasi dari literal string multi-baris di Python, jadi alat yang memproses dokumentasi harus menghapus indentasi jika diinginkan. Ini dilakukan dengan menggunakan konvensi berikut. Baris tidak kosong pertama setelah baris pertama string menentukan jumlah lekukan untuk seluruh string dokumentasi. (Kita tidak dapat menggunakan baris pertama karena biasanya bersebelahan dengan tanda kutip pembuka string sehingga indentasinya tidak terlihat dalam literal string.) Spasi "setara" dengan indentasi ini kemudian dihapus dari awal semua baris string . Garis yang indentasinya lebih kecil tidak boleh muncul, tetapi jika muncul, semua spasi putih di depannya harus dihilangkan. Kesetaraan spasi harus diuji setelah penambahan tab (biasanya menjadi 8 spasi).

4.8.8. Function Annotations

Anotasi fungsi adalah informasi metadata yang sepenuhnya opsional tentang jenis yang digunakan oleh fungsi yang ditentukan pengguna (lihatPEP 3107 dan PEP 484 untuk informasi lebih lanjut).Anotasi disimpan dalam__annotations__ atribut fungsi sebagai kamus dan tidak berpengaruh pada bagian lain dari fungsi tersebut. Anotasi parameter ditentukan oleh tanda titik dua setelah nama parameter, diikuti dengan ekspresi yang mengevaluasi nilai anotasi. Anotasi pengembalian ditentukan oleh literal->, diikuti oleh ekspresi, antara daftar parameter dan titik dua yang menunjukkan akhir pernyataandef.

4.9. Intermezzo: Coding Style

Sekarang Anda akan menulis potongan Python yang lebih panjang dan lebih kompleks, inilah saat yang tepat untuk berbicara tentang gaya pengkodean . Sebagian besar bahasa dapat ditulis (atau lebih ringkas, diformat ) dalam gaya yang berbeda; beberapa lebih mudah dibaca daripada yang lain. Memudahkan orang lain untuk membaca kode Anda selalu merupakan ide yang bagus, dan mengadopsi gaya pengkodean yang bagus sangat membantu untuk itu.
Untuk Piton,PEP 8 telah muncul sebagai panduan gaya yang dipatuhi sebagian besar proyek; itu mempromosikan gaya pengkodean yang sangat mudah dibaca dan menyenangkan mata. Setiap pengembang Python harus membacanya di beberapa titik; berikut adalah poin terpenting yang diekstraksi untuk Anda:
