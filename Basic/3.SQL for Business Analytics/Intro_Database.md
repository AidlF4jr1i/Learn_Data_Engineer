# Memahami Database dan SQL

Berikut adalah panduan lengkap untuk memahami konsep dasar database dan cara berinteraksi dengannya menggunakan SQL.

### **1. Apa itu Database? 🗄️**

* **Database** (Basis Data) adalah kumpulan data terstruktur yang disimpan secara sistematis di dalam komputer agar dapat diolah, diakses, dan dikelola dengan mudah.
* Untuk mengelolanya, kita menggunakan software bernama **DBMS (Database Management System)**. Anggap saja DBMS ini sebagai "manajer" data Anda. Contoh populer: MySQL, PostgreSQL, dan Microsoft SQL Server.

---

### **2. Relational Database (RDMS)**

* **Relational Database** adalah jenis database paling umum, di mana data disimpan dalam bentuk **tabel-tabel** yang saling berhubungan.
* Setiap tabel terdiri dari **baris (records)** dan **kolom (fields)**.
    * **Kolom**: Atribut data (contoh: `Nama_Siswa`, `Kelas`).
    * **Baris**: Entitas data tunggal (contoh: data lengkap siswa bernama 'Budi').

---

### **3. Analogi Sederhana: Lemari Arsip**

* **Server Database** → Perpustakaan (Gedung utama).
* **Database** → Lemari Arsip (Misal: Lemari "Data Siswa").
* **Tabel** → Laci di dalam Lemari (Misal: Laci "Siswa Kelas 10").
* **Baris (Record)** → Map di dalam Laci (Data lengkap satu siswa).
* **Kolom (Field)** → Isi data di dalam map (Nama, Alamat, dll).

---

### **4. SQL (Structured Query Language)**

Untuk "berkomunikasi" dengan database (meminta, menambah, mengubah data), kita menggunakan bahasa standar bernama **SQL**. SQL adalah jembatan antara Anda dan database.

---

### **5. Membedah Perintah `SELECT`**

`SELECT` adalah perintah dasar untuk **memilih dan menampilkan data** dari tabel. Mari kita lihat berbagai variasinya.

* **Menampilkan SEMUA KOLOM dari satu tabel**
    Tanda bintang (`*`) adalah *wildcard* yang berarti "semua kolom".
    ```sql
    SELECT * FROM Siswa;
    ```
    *(**Catatan:** Setiap akhir perintah SQL, pastikan menambahkan titik koma `;`!)*

* **Menampilkan KOLOM TERTENTU saja**
    Jika hanya butuh beberapa kolom, sebutkan namanya dipisahkan dengan koma.
    ```sql
    SELECT Nama_Lengkap, Kelas FROM Siswa;
    ```

* **Membuat KOLOM KALKULASI dengan Alias (`AS`)**
    Kita bisa melakukan operasi matematika pada kolom dan memberinya nama baru (alias) menggunakan `AS`.
    ```sql
    SELECT nama_produk, harga, harga * 0.1 AS ppn FROM Produk;
    ```
    Query ini akan menampilkan kolom baru bernama `ppn` yang isinya adalah 10% dari kolom `harga`.

* **Membatasi Jumlah BARIS yang Ditampilkan (`LIMIT`)**
    Gunakan `LIMIT` untuk menampilkan hanya beberapa baris pertama dari hasil query.
    ```sql
    SELECT * FROM Siswa LIMIT 5;
    ```
    Query ini hanya akan menampilkan 5 baris pertama dari tabel `Siswa`.

* **Menampilkan Nilai Unik (`DISTINCT`)**
    Gunakan `DISTINCT` pada sebuah kolom untuk menghilangkan data duplikat dan hanya menampilkan nilai yang unik.
    ```sql
    SELECT DISTINCT Kota_Asal FROM Siswa;
    ```
    Jika ada 10 siswa dari Jakarta, kata 'Jakarta' hanya akan muncul satu kali.

* **Mengurutkan Hasil (`ORDER BY`)**
    Gunakan `ORDER BY` untuk mengurutkan hasil berdasarkan kolom tertentu.
    * **`ASC` (Ascending):** Mengurutkan dari terkecil ke terbesar (A-Z, 1-100). Ini adalah default jika tidak ditulis.
    * **`DESC` (Descending):** Mengurutkan dari terbesar ke terkecil (Z-A, 100-1).

    ```sql
    -- Mengurutkan siswa berdasarkan nama secara A-Z
    SELECT * FROM Siswa ORDER BY Nama_Lengkap ASC;

    -- Mengurutkan siswa berdasarkan kelas secara Z-A
    SELECT * FROM Siswa ORDER BY Kelas DESC;
    ```

---

### **6. Menyaring Data dengan `WHERE`**

`WHERE` adalah klausa untuk memfilter baris dan menampilkan data yang hanya memenuhi kondisi tertentu.

* **Filter dengan Operator Perbandingan (`>`, `<`, `=`)**
    Menampilkan semua karyawan yang lahir setelah 1 Januari 1970.
    ```sql
    SELECT * FROM employee WHERE birth_day > '1970-01-01';
    ```

* **Filter dengan Beberapa Kondisi (`AND`, `OR`)**
    Menampilkan karyawan laki-laki (`male`) **DAN** gajinya di atas 75000.
    ```sql
    SELECT * FROM employee WHERE sex = 'male' AND salary > 75000;
    ```

* **Filter Berdasarkan Daftar Nilai (`IN`, `NOT IN`)**
    Menampilkan karyawan yang `super_id`-nya ada di dalam daftar (`102` atau `106`). Gunakan `NOT IN` untuk menampilkan selain yang ada di daftar.
    ```sql
    SELECT * FROM employee WHERE super_id IN (102, 106);
    ```

* **Filter Berdasarkan Pola Teks (`LIKE`, `NOT LIKE`)**
    Menampilkan karyawan yang nama depannya diawali huruf `J`. `%` adalah *wildcard* yang mewakili karakter apa pun.
    ```sql
    SELECT * FROM employee WHERE firstname LIKE 'J%';
    ```
    **Pola `LIKE` yang Umum:**
    * `'A%'` → Teks yang **diawali** dengan 'A'.
    * `'%N'` → Teks yang **diakhiri** dengan 'N'.
    * `'%AN%'`→ Teks yang **mengandung** 'AN' di dalamnya.
    * `'_A%'` → Teks yang memiliki huruf 'A' di **posisi kedua**.

* **Filter Berdasarkan Rentang Nilai (`BETWEEN`, `NOT BETWEEN`)**
    Menampilkan karyawan yang gajinya berada di antara 50000 dan 75000 (inklusif). Gunakan `NOT BETWEEN` untuk menampilkan data di luar rentang tersebut.
    ```sql
    SELECT * FROM employee WHERE salary BETWEEN 50000 AND 75000;
    ```

# Aggreagtion, Group BY, and WIndows Function

