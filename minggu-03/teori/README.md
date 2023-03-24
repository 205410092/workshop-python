    BAB 5

5. Data Structures

Bab ini menjelaskan beberapa hal yang telah Anda pelajari secara lebih mendetail, dan menambahkan beberapa hal baru juga.

5.1. More on Lists

Tipe data daftar memiliki beberapa metode lagi.
Berikut ini semua metode objek daftar:
- list.append(x)

Tambahkan item ke akhir daftar. Setara dengan .a[len(a):] = [x]

- list.extend(iterable)

Perpanjang daftar dengan menambahkan semua item dari iterable. Setara dengan .a[len(a):] = iterable

- list.insert(i, x)

Masukkan item pada posisi tertentu. Argumen pertama adalah indeks elemen sebelum disisipkan, jadi sisipkan di bagian depan daftar, dan sama dengan .a.insert(0, x)a.insert(len(a), x)a.append(x)

- list.remove(x)

Hapus item pertama dari daftar yang nilainya sama dengan x . Itu memunculkan ValueErrorjika tidak ada item seperti itu.

- list.pop([i])

Hapus item pada posisi yang diberikan dalam daftar, dan kembalikan. Jika tidak ada indeks yang ditentukan, a.pop()hapus dan kembalikan item terakhir dalam daftar. (Kurung siku di sekitar i pada tanda tangan metode menunjukkan bahwa parameternya opsional, bukan berarti Anda harus mengetikkan tanda kurung siku pada posisi itu. Anda akan sering melihat notasi ini di Referensi Pustaka Python.)

- list.clear()

Hapus semua item dari daftar. Setara dengan .del a[:]

- list.index(x[, start[, end]])

Kembalikan indeks berbasis nol dalam daftar item pertama yang nilainya sama dengan x . Menaikkan a ValueErrorjika tidak ada item seperti itu.
Argumen opsional awal dan akhir diinterpretasikan seperti dalam notasi irisan dan digunakan untuk membatasi pencarian ke urutan tertentu dari daftar. Indeks yang dikembalikan dihitung relatif terhadap awal urutan penuh daripada argumen awal.

- list.count(x)

Kembalikan berapa kali x muncul dalam daftar.

- list.sort(*, key=None, reverse=False)

Sortir item daftar pada tempatnya (argumen dapat digunakan untuk mengurutkan kustomisasi, lihat sorted()penjelasannya).

- list.reverse()

Balikkan elemen daftar pada tempatnya.

- list.copy()

Kembalikan salinan daftar yang dangkal. Setara dengan a[:].

5.1.1. Using Lists as Stacks

Metode daftar membuatnya sangat mudah untuk menggunakan daftar sebagai tumpukan, di mana elemen terakhir yang ditambahkan adalah elemen pertama yang diambil (“last-in, first-out”). Untuk menambahkan item ke atas tumpukan, gunakan append(). Untuk mengambil item dari atas tumpukan, gunakan pop()tanpa indeks eksplisit.

5.1.2. Using Lists as Queues

Dimungkinkan juga untuk menggunakan daftar sebagai antrian, di mana elemen pertama yang ditambahkan adalah elemen pertama yang diambil (“first-in, first-out”); namun, daftar tidak efisien untuk tujuan ini. Sementara menambahkan dan muncul dari akhir daftar cepat, melakukan sisipan atau muncul dari awal daftar lambat (karena semua elemen lain harus digeser satu).

5.1.3. List Comprehensions

Pemahaman daftar menyediakan cara ringkas untuk membuat daftar. Aplikasi umum adalah membuat daftar baru di mana setiap elemen adalah hasil dari beberapa operasi yang diterapkan ke setiap anggota urutan lain atau iterable, atau untuk membuat urutan elemen yang memenuhi kondisi tertentu.

5.1.4. Nested List Comprehensions

Ekspresi awal dalam pemahaman daftar dapat berupa sembarang ekspresi, termasuk pemahaman daftar lainnya.

5.2. The del statement

Ada cara untuk menghapus item dari daftar yang diberikan indeksnya alih-alih nilainya: pernyataan del. Ini berbeda dari pop()metode yang mengembalikan nilai. Pernyataan itu deljuga dapat digunakan untuk menghapus irisan dari daftar atau menghapus seluruh daftar (yang kita lakukan sebelumnya dengan menugaskan daftar kosong ke irisan).

5.3. Tuples and Sequences

Kami melihat bahwa daftar dan string memiliki banyak properti umum, seperti operasi pengindeksan dan pemotongan. Mereka adalah dua contoh tipe data sequence (lihat Tipe Sequence — list, tuple, range ). Karena Python adalah bahasa yang berkembang, tipe data urutan lainnya dapat ditambahkan. Ada juga tipe data urutan standar lainnya: tuple.
Sebuah tuple terdiri dari sejumlah nilai yang dipisahkan dengan koma
Seperti yang Anda lihat, pada tupel keluaran selalu tertutup dalam tanda kurung, sehingga tupel bersarang diinterpretasikan dengan benar; mereka mungkin dimasukkan dengan atau tanpa tanda kurung di sekitarnya, meskipun seringkali tanda kurung diperlukan (jika tuple adalah bagian dari ekspresi yang lebih besar). Tidak mungkin menetapkan ke masing-masing item tupel, namun dimungkinkan untuk membuat tupel yang berisi objek yang dapat diubah, seperti daftar.

5.4. Sets

Python juga menyertakan tipe data untuk sets . Himpunan adalah koleksi tak terurut tanpa elemen duplikat. Penggunaan dasar termasuk pengujian keanggotaan dan menghilangkan entri duplikat. Set objek juga mendukung operasi matematika seperti penyatuan, persimpangan, perbedaan, dan perbedaan simetris.

Kurung kurawal atau set()fungsi dapat digunakan untuk membuat himpunan. Catatan: untuk membuat himpunan kosong Anda harus menggunakan set(), bukan {}; yang terakhir membuat kamus kosong, struktur data yang akan kita bahas di bagian selanjutnya.

5.5. Dictionaries

Tipe data berguna lainnya yang dibangun ke dalam Python adalah kamus (lihat Jenis Pemetaan — dict ). Kamus terkadang ditemukan dalam bahasa lain sebagai "memori asosiatif" atau "array asosiatif". Tidak seperti urutan, yang diindeks oleh rentang angka, kamus diindeks oleh key , yang dapat berupa tipe apa pun yang tidak dapat diubah; string dan angka selalu bisa menjadi kunci. Tupel dapat digunakan sebagai kunci jika hanya berisi string, angka, atau tupel; jika tuple berisi objek yang dapat diubah baik secara langsung maupun tidak langsung, itu tidak dapat digunakan sebagai kunci. Anda tidak dapat menggunakan daftar sebagai kunci, karena daftar dapat dimodifikasi menggunakan penetapan indeks, penetapan irisan, atau metode seperti append()dan extend().

Yang terbaik adalah menganggap kamus sebagai sekumpulan kunci: pasangan nilai, dengan persyaratan bahwa kuncinya unik (dalam satu kamus). Sepasang kawat gigi membuat kamus kosong: {}. Menempatkan daftar pasangan kunci:nilai yang dipisahkan koma di dalam kurung kurawal akan menambahkan pasangan kunci:nilai awal ke kamus; ini juga cara kamus ditulis pada output.

5.6. Looping Techniques

Saat mengulang kamus, kunci dan nilai yang sesuai dapat diambil pada saat yang sama menggunakan items()metode ini.

5.7. More on Conditions

Kondisi yang digunakan dalam whiledan ifpernyataan dapat berisi operator apa pun, bukan hanya perbandingan.
Operator pembanding indan adalah pengujian keanggotaan yang menentukan apakah suatu nilai ada di dalam (atau tidak di dalam) wadah. Operator dan membandingkan apakah dua objek benar-benar objek yang sama. Semua operator pembanding memiliki prioritas yang sama, yang lebih rendah dari semua operator numerik.not inisis not

Perbandingan dapat dirantai. Misalnya, menguji apakah kurang dari dan terlebih lagi sama dengan .a < b == cabbc

Perbandingan dapat digabungkan menggunakan operator Boolean anddan or, dan hasil perbandingan (atau ekspresi Boolean lainnya) dapat ditiadakan dengan not. Ini memiliki prioritas lebih rendah daripada operator pembanding; di antara mereka, notmemiliki prioritas tertinggi dan orterendah, sehingga setara dengan . Seperti biasa, tanda kurung dapat digunakan untuk menyatakan komposisi yang diinginkan.A and not B or C(A and (not B)) or C

Operator Boolean anddan ordisebut operator hubung singkat : argumen mereka dievaluasi dari kiri ke kanan, dan evaluasi berhenti segera setelah hasilnya ditentukan. Misalnya, jika Adan Cbenar tetapi Bsalah, tidak mengevaluasi ekspresi . Ketika digunakan sebagai nilai umum dan bukan sebagai Boolean, nilai kembalian dari operator hubung singkat adalah argumen terakhir yang dievaluasi.A and B and CC

Dimungkinkan untuk menetapkan hasil perbandingan atau ekspresi Boolean lainnya ke variabel.

5.8. Comparing Sequences and Other Types

Objek urutan biasanya dapat dibandingkan dengan objek lain dengan tipe urutan yang sama. Perbandingannya menggunakan leksikografispengurutan: pertama dua item pertama dibandingkan, dan jika berbeda, ini menentukan hasil perbandingan; jika sama, dua item berikutnya dibandingkan, dan seterusnya, sampai salah satu urutannya habis. Jika dua item yang akan dibandingkan itu sendiri adalah urutan dari jenis yang sama, perbandingan leksikografis dilakukan secara rekursif. Jika semua item dari dua urutan sebanding, urutannya dianggap sama. Jika satu urutan adalah sub-urutan awal dari yang lain, urutan yang lebih pendek adalah yang lebih kecil (lebih kecil). Pengurutan leksikografis untuk string menggunakan nomor poin kode Unicode untuk mengurutkan karakter individual.
Perhatikan bahwa membandingkan objek dari jenis yang berbeda dengan <atau >legal asalkan objek tersebut memiliki metode perbandingan yang sesuai. Misalnya, tipe numerik campuran dibandingkan berdasarkan nilai numeriknya, jadi 0 sama dengan 0,0, dll. Jika tidak, alih-alih memberikan pengurutan arbitrer, penafsir akan memunculkan pengecualian TypeError.
