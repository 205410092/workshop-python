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
