PEP-249, dokumentasi psycopg, PyMongo, SQLAlchemy. Kerjakan dan jelaskan akses ke basis data CockroachDB menggunakan psycopg2 dan menggunakan SQLAlchemy

Bangun Aplikasi Python dengan CockroachDB dan psycopg2

Langkah 1. Mulai CockroachDB

Pilih metode instalasi Anda

Anda dapat membuat klaster Tanpa Server CockroachDB menggunakan CockroachDB Cloud Console, alat antarmuka pengguna grafis (GUI) berbasis web, atau ccloud, alat antarmuka baris perintah (CLI).

Langkah 2. Dapatkan kode contoh

git clone https://github.com/cockroachlabs/hello-world-python-psycopg2

Kode sampel dalam example.pymelakukan hal berikut:

Membuat accountstabel dan menyisipkan beberapa baris

Transfer dana antara dua akun di dalam transaksi

Menghapus akun dari tabel sebelum keluar sehingga Anda dapat menjalankan kembali kode contoh

Untuk menangani kesalahan percobaan ulang transaksi , kode menggunakan loop percobaan ulang tingkat aplikasi yang, jika terjadi kesalahan, akan tidur sebelum mencoba transfer dana lagi. Jika menemukan kesalahan coba lagi, ia tidur untuk interval yang lebih lama, menerapkan backoff eksponensial .

Langkah 3. Instal driver psycopg2

Untuk menginstal psycopg2-binary, jalankan perintah berikut:

pip install psycopg2-binary

Langkah 4. Jalankan kode

=> Setel DATABASE_URLvariabel lingkungan ke string koneksi ke klaster Anda:

export DATABASE_URL="{connection-string}"

Di mana {connection-string}string koneksi yang Anda salin sebelumnya.

Aplikasi menggunakan string koneksi yang disimpan ke DATABASE_URLvariabel lingkungan untuk terhubung ke klaster Anda dan menjalankan kode.

=> Jalankan kode:

cd hello-world-python-psycopg2

python example.py

Output harus menunjukkan saldo akun sebelum dan sesudah transfer dana:

Balances at Thu Aug  4 15:51:03 2022:
account id: 2e964b45-2034-49a7-8ab8-c5d0082b71f1  balance: $1000
account id: 889cb1eb-b747-46f4-afd0-15d70844147f  balance: $250
Balances at Thu Aug  4 15:51:03 2022:
account id: 2e964b45-2034-49a7-8ab8-c5d0082b71f1  balance: $900
account id: 889cb1eb-b747-46f4-afd0-15d70844147f  balance: $350
