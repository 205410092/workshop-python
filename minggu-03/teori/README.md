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
