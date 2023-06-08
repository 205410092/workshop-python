BAB 9

9. Classes

Kelas menyediakan sarana bundling data dan fungsionalitas bersama. Membuat kelas baru akan membuat tipe objek baru, yang memungkinkan instance baru dari tipe tersebut dibuat. Setiap instance kelas dapat memiliki atribut yang melekat padanya untuk mempertahankan statusnya. Instance kelas juga dapat memiliki metode (ditentukan oleh kelasnya) untuk memodifikasi statusnya.
Dibandingkan dengan bahasa pemrograman lain, mekanisme kelas Python menambahkan kelas dengan sintaks dan semantik baru yang minimal. Ini adalah campuran dari mekanisme kelas yang ditemukan di C++ dan Modula-3. Kelas Python menyediakan semua fitur standar Pemrograman Berorientasi Objek: mekanisme pewarisan kelas memungkinkan banyak kelas dasar, kelas turunan dapat mengganti metode apa pun dari kelas atau kelas dasarnya, dan metode dapat memanggil metode kelas dasar dengan nama yang sama . Objek dapat berisi jumlah dan jenis data yang sewenang-wenang. Seperti halnya modul, kelas mengambil bagian dari sifat dinamis Python: mereka dibuat saat runtime, dan dapat dimodifikasi lebih lanjut setelah dibuat.

9.1. A Word About Names and Objects

Objek memiliki individualitas, dan banyak nama (dalam berbagai cakupan) dapat terikat ke objek yang sama. Ini dikenal sebagai aliasing dalam bahasa lain. Ini biasanya tidak dihargai pada pandangan pertama di Python, dan dapat diabaikan dengan aman ketika berhadapan dengan tipe dasar yang tidak dapat diubah (angka, string, tupel). Namun, aliasing mungkin memiliki efek yang mengejutkan pada semantik kode Python yang melibatkan objek yang dapat diubah seperti daftar, kamus, dan sebagian besar jenis lainnya. Ini biasanya digunakan untuk kepentingan program, karena alias berperilaku seperti penunjuk dalam beberapa hal. Misalnya, melewatkan objek itu murah karena hanya sebuah pointer yang dilewatkan oleh implementasi; dan jika sebuah fungsi memodifikasi objek yang diteruskan sebagai argumen, pemanggil akan melihat perubahannya — ini menghilangkan kebutuhan akan dua mekanisme penerusan argumen yang berbeda seperti di Pascal.

9.2. Python Scopes and Namespaces

Sebelum memperkenalkan kelas, pertama-tama saya harus memberi tahu Anda sesuatu tentang aturan ruang lingkup Python. Definisi kelas memainkan beberapa trik rapi dengan ruang nama, dan Anda perlu mengetahui cara kerja ruang lingkup dan ruang nama untuk memahami sepenuhnya apa yang terjadi. Kebetulan, pengetahuan tentang subjek ini berguna untuk semua programmer Python tingkat lanjut.
Mari kita mulai dengan beberapa definisi.
Namespace adalah pemetaan dari nama ke objek . Sebagian besar ruang nama saat ini diimplementasikan sebagai kamus Python, tetapi biasanya tidak terlihat dengan cara apa pun (kecuali untuk kinerja), dan mungkin berubah di masa mendatang. Contoh ruang nama adalah: kumpulan nama bawaan (berisi fungsi seperti abs(), dan nama pengecualian bawaan); nama global dalam modul; dan nama lokal dalam pemanggilan fungsi. Dalam arti himpunan atribut suatu objek juga membentuk namespace. Hal penting yang harus diketahui tentang ruang nama adalah sama sekali tidak ada hubungan antara nama di ruang nama yang berbeda; misalnya, dua modul berbeda dapat mendefinisikan fungsi maximizetanpa kebingungan — pengguna modul harus mengawalinya dengan nama modul.

9.3. A First Look at Classes

Kelas memperkenalkan sedikit sintaks baru, tiga tipe objek baru, dan beberapa semantik baru.

9.3.1. Class Definition Syntax

Definisi kelas, seperti definisi fungsi ( defpernyataan) harus dieksekusi sebelum memiliki efek apa pun. (Anda dapat menempatkan definisi kelas di cabang pernyataan if, atau di dalam fungsi.)
Dalam praktiknya, pernyataan di dalam definisi kelas biasanya berupa definisi fungsi, tetapi pernyataan lain diperbolehkan, dan terkadang berguna — kita akan membahasnya lagi nanti. Definisi fungsi di dalam kelas biasanya memiliki bentuk daftar argumen yang khas, ditentukan oleh konvensi pemanggilan metode — sekali lagi, ini akan dijelaskan nanti.
Saat definisi kelas dimasukkan, namespace baru dibuat, dan digunakan sebagai cakupan lokal — jadi, semua penugasan ke variabel lokal masuk ke namespace baru ini. Secara khusus, definisi fungsi mengikat nama fungsi baru di sini.

9.3.2. Class Objects

Objek kelas mendukung dua jenis operasi: referensi atribut dan instantiasi.

9.3.3. Instance Objects

Sekarang apa yang bisa kita lakukan dengan objek instan? Satu-satunya operasi yang dipahami oleh objek instan adalah referensi atribut. Ada dua jenis nama atribut yang valid: atribut data dan metode.
atribut data sesuai dengan "variabel instan" di Smalltalk, dan dengan "anggota data" di C++. Atribut data tidak perlu dideklarasikan; seperti variabel lokal, mereka muncul saat pertama kali ditugaskan.

9.3.4. Method Objects

Biasanya, sebuah metode dipanggil tepat setelah terikat:
x.f()
Dalam MyClasscontoh, ini akan mengembalikan string . Namun, tidak perlu memanggil metode segera: adalah objek metode, dan dapat disimpan dan dipanggil di lain waktu. Misalnya:'hello world'x.f
xf = x.f
while True:
    print(xf())
akan terus dicetak hingga akhir waktu.hello world

9.3.5. Class and Instance Variables

Secara umum, variabel instan untuk data unik untuk setiap instans dan variabel kelas untuk atribut dan metode yang digunakan bersama oleh semua instans kelas.

9.4. Random Remarks

Atribut data dapat direferensikan oleh metode maupun oleh pengguna biasa ("klien") dari suatu objek. Dengan kata lain, kelas tidak dapat digunakan untuk mengimplementasikan tipe data abstrak murni. Nyatanya, tidak ada apa pun dalam Python yang memungkinkan untuk memaksakan penyembunyian data — semuanya didasarkan pada konvensi. (Di sisi lain, implementasi Python, yang ditulis dalam C, dapat sepenuhnya menyembunyikan detail implementasi dan mengontrol akses ke objek jika perlu; ini dapat digunakan oleh ekstensi ke Python yang ditulis dalam C.)

9.5. Inheritance

Tentu saja, fitur bahasa tidak akan layak disebut "kelas" tanpa mendukung pewarisan. Sintaks untuk definisi kelas turunan terlihat seperti ini:
class DerivedClassName(BaseClassName):
    <statement-1>
    .
    .
    .
    <statement-N>
Nama BaseClassNameharus didefinisikan dalam ruang lingkup yang berisi definisi kelas turunan. Di tempat nama kelas dasar, ekspresi sewenang-wenang lainnya juga diperbolehkan. Ini bisa berguna, misalnya, ketika kelas dasar didefinisikan dalam modul lain:
class DerivedClassName(modname.BaseClassName):
Eksekusi definisi kelas turunan berjalan sama seperti untuk kelas dasar. Ketika objek kelas dibangun, kelas dasar diingat. Ini digunakan untuk menyelesaikan referensi atribut: jika atribut yang diminta tidak ditemukan di kelas, pencarian berlanjut untuk mencari di kelas dasar. Aturan ini diterapkan secara rekursif jika kelas dasar itu sendiri berasal dari beberapa kelas lain.

9.5.1. Multiple Inheritance

Python juga mendukung bentuk pewarisan berganda.
Untuk sebagian besar tujuan, dalam kasus yang paling sederhana, Anda dapat memikirkan pencarian atribut yang diwarisi dari kelas induk sebagai kedalaman pertama, kiri ke kanan, bukan pencarian dua kali di kelas yang sama di mana ada tumpang tindih dalam hierarki. Jadi, jika atribut tidak ditemukan di DerivedClassName, dicari di Base1, kemudian (secara rekursif) di kelas dasar Base1, dan jika tidak ditemukan di sana, dicari di Base2, dan seterusnya.
Nyatanya, ini sedikit lebih rumit dari itu; urutan resolusi metode berubah secara dinamis untuk mendukung panggilan kooperatif ke super(). Pendekatan ini dikenal dalam beberapa bahasa pewarisan ganda lainnya sebagai metode panggilan-berikutnya dan lebih kuat daripada panggilan super yang ditemukan dalam bahasa pewarisan tunggal.

9.6. Private Variables

Variabel instan "Pribadi" yang tidak dapat diakses kecuali dari dalam objek tidak ada di Python. Namun, ada konvensi yang diikuti oleh sebagian besar kode Python: nama yang diawali dengan garis bawah (misalnya _spam) harus diperlakukan sebagai bagian non-publik dari API (apakah itu fungsi, metode, atau anggota data). Ini harus dianggap sebagai detail implementasi dan dapat berubah tanpa pemberitahuan.

9.7. Odds and Ends

Kadang-kadang berguna untuk memiliki tipe data yang mirip dengan Pascal "record" atau C "struct", menggabungkan beberapa item data bernama.
Sepotong kode Python yang mengharapkan tipe data abstrak tertentu seringkali dapat diteruskan ke kelas yang mengemulasi metode dari tipe data tersebut. Misalnya, jika Anda memiliki fungsi yang memformat beberapa data dari objek file, Anda dapat mendefinisikan kelas dengan metode read()dan readline()mendapatkan data dari buffer string, dan meneruskannya sebagai argumen.

9.8. Iterators

Gaya akses ini jelas, ringkas, dan nyaman. Penggunaan iterator meliputi dan menyatukan Python. Di belakang layar, forpernyataan itu memanggil iter()objek kontainer. Fungsi mengembalikan objek iterator yang mendefinisikan metode __next__()yang mengakses elemen dalam wadah satu per satu. Ketika tidak ada lagi elemen, __next__()munculkan StopIterationpengecualian yang memberi tahu forloop untuk diakhiri.

9.9. Generators

Generator adalah alat yang sederhana dan kuat untuk membuat iterator. Mereka ditulis seperti fungsi biasa tetapi menggunakanyieldpernyataan kapan pun mereka ingin mengembalikan data. Setiap kalinext()dipanggil, generator melanjutkan di mana ia tinggalkan (mengingat semua nilai data dan pernyataan mana yang terakhir dieksekusi).

9.10. Generator Expressions

Beberapa generator sederhana dapat dikodekan secara ringkas sebagai ekspresi menggunakan sintaks yang mirip dengan pemahaman daftar tetapi dengan tanda kurung, bukan tanda kurung siku. Ekspresi ini dirancang untuk situasi di mana generator langsung digunakan oleh fungsi penutup. Ekspresi generator lebih kompak tetapi kurang fleksibel daripada definisi generator lengkap dan cenderung lebih ramah memori daripada pemahaman daftar yang setara.
