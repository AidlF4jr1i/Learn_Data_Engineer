# Memahami Subprogram: Fungsi dan Prosedur dalam Python

Selamat datang di panduan lengkap untuk memahami **subprogram** dalam Python! Dalam dunia pemrograman, efisiensi adalah kunci. Menulis kode yang sama berulang kali tidak hanya membuang waktu, tetapi juga membuat program sulit untuk dikelola. Materi ini akan memandu Anda untuk memahami cara kerja **fungsi** dan **prosedur**, dua jenis subprogram yang memungkinkan Anda menulis kode yang lebih bersih, modular, dan dapat digunakan kembali (*reusable*). Kita akan membahas mulai dari konsep dasar, sintaksis, berbagai jenis parameter, hingga praktik terbaik seperti dokumentasi dan pembuatan modul.

---

## Subprogram

Bayangkan Anda sedang membangun program yang besar. Seiring waktu, Anda akan menemukan bagian-bagian kode yang melakukan tugas yang sama di banyak tempat. Misalnya, sebuah rumus perhitungan. Mari kita lihat contoh sederhana:

```python
# Luas pertama
panjang = 5
lebar = 10
luas_persegi_panjang = panjang * lebar
print(luas_persegi_panjang)

# Luas kedua
panjang = 4
lebar = 15
luas_persegi_panjang = panjang * lebar
print(luas_persegi_panjang)
```

**Output:**
```
50
60
```

Perhatikan bahwa kita menulis rumus `panjang * lebar` dua kali. Bagaimana jika kita perlu menghitung luas untuk sepuluh atau seratus persegi panjang yang berbeda? Tentu akan sangat tidak efisien.

Lalu, adakah cara untuk menghindari pengetikan kode berulang dan sebaliknya, dapat digunakan berkali-kali? Jawabannya adalah **ada**. Inilah yang disebut sebagai **subprogram**, dan salah satu jenisnya yang paling umum adalah **fungsi**.

Lihat bagaimana kode di atas menjadi lebih ringkas dengan fungsi:

```python
def mencari_luas_persegi_panjang(panjang, lebar):
    luas_persegi_panjang = panjang * lebar
    return luas_persegi_panjang

persegi_panjang_pertama = mencari_luas_persegi_panjang(5, 10)
print(persegi_panjang_pertama)

persegi_panjang_kedua = mencari_luas_persegi_panjang(4, 15)
print(persegi_panjang_kedua)
```

**Output:**
```
50
60
```

Jauh lebih rapi, bukan? Blok kode yang dimulai dari `def` hingga `return` adalah sebuah fungsi.

Secara formal, **subprogram** adalah serangkaian instruksi yang dirancang untuk melakukan operasi spesifik yang sering digunakan dalam suatu program. Dua jenis subprogram yang paling umum adalah:

1.  **Fungsi**: Blok kode yang dapat menerima input, melakukan pemrosesan, dan **mengembalikan sebuah nilai** (output). Tipe data dari nilai yang dikembalikan ini bisa ditentukan secara eksplisit (misalnya, `integer`, `string`, dll.).
2.  **Prosedur**: Mirip dengan fungsi, tetapi **tidak mengembalikan nilai**. Prosedur menjalankan serangkaian instruksi dan selesai. Keadaan awal (*initial state*) dan keadaan akhir (*final state*) dari prosedur ini jelas.

---

## Fungsi

### Analogi Fungsi dalam Matematika

Fungsi dalam pemrograman terinspirasi dari fungsi matematika, yaitu pemetaan antara dua himpunan nilai: **domain** (input) dan **range** (output). Anda bisa membayangkannya sebagai mesin yang menerima input dan menghasilkan output yang sesuai.

Notasi yang umum adalah: `f(x) = 2x`
* **f**: Nama fungsi.
* **x**: Input (domain).
* **2x**: Aturan pemrosesan untuk menghasilkan output (range).

### Fungsi dalam Pemrograman

**Fungsi** dalam pemrograman adalah blok kode yang dapat digunakan kembali untuk menjalankan fungsionalitas tertentu saat dipanggil. Di Python, fungsi terbagi menjadi dua jenis utama:

#### 1. Built-in Functions
Fungsi bawaan (`built-in functions`) adalah fungsi yang sudah terintegrasi dalam Python, sehingga Anda bisa langsung menggunakannya tanpa perlu mengimpor *library* atau modul apa pun. Contohnya termasuk `print()`, `len()`, `type()`, dan `range()`.

#### 2. User-defined Functions
Fungsi yang didefinisikan pengguna (`user-defined functions`) adalah fungsi yang Anda buat sendiri untuk melakukan tugas spesifik, seperti contoh `mencari_luas_persegi_panjang()` yang kita buat sebelumnya.

```python
# Contoh User-defined Function
def mencari_luas_persegi_panjang(panjang, lebar):
    luas_persegi_panjang = panjang * lebar
    return luas_persegi_panjang
```

### Library, Modul, dan Package

Terkadang, fungsi bawaan saja tidak cukup. Di sinilah *library* berperan.

* **Modul**: Sebuah file Python (`.py`) yang berisi kumpulan fungsi, kelas, dan variabel. Contoh: `math`, atau file `hello.py` yang akan kita buat nanti.
* **Package**: Sebuah direktori yang berisi satu atau lebih modul yang saling terkait. Contoh: `NumPy` dan `Pandas`.
* **Library**: Istilah umum untuk koleksi modul dan *package* yang menyediakan fungsionalitas tertentu.

Library dalam Python terbagi menjadi dua jenis:

1.  **Python Standard Library**: Library yang sudah terpasang otomatis saat Anda menginstal Python. Library ini berisi modul-modul penting seperti `os`, `datetime`, dan `re`. Anda bisa langsung menggunakannya dengan `import`. Kunjungi [dokumentasi resmi](https://docs.python.org/3/library/) untuk melihat daftarnya.
2.  **External Library**: Library yang dikembangkan oleh pihak ketiga dan perlu diinstal terlebih dahulu (biasanya menggunakan `pip`). Contoh populernya adalah `TensorFlow` untuk *machine learning* atau `Requests` untuk interaksi HTTP.

### Manfaat Fungsi

Mengapa kita harus menggunakan fungsi?
1.  **Modularitas**: Program dapat dipecah menjadi bagian-bagian yang lebih kecil dan mudah dikelola.
2.  **Dapat Digunakan Kembali (*Reusability*)**: Hindari penulisan ulang kode yang sama. Cukup panggil fungsinya.
3.  **Pengujian Mudah**: Setiap fungsi bersifat independen dan dapat diuji secara terpisah, mempermudah *debugging* dan kolaborasi tim.

### Mendefinisikan Fungsi dalam Python

Secara umum, sebuah fungsi terdiri dari tiga bagian utama:

```python
def mencari_luas_persegi_panjang(panjang, lebar):  #---> Function Header
    luas_persegi_panjang = panjang * lebar      #---> Function Body
    return luas_persegi_panjang                 #---> Function Return
```

* **Function Header**: Baris pertama yang diawali dengan `def`. Ini memberitahu Python bahwa Anda sedang mendefinisikan sebuah fungsi.
* **Function Body**: Blok kode di bawah *header* (dengan indentasi) yang berisi logika atau instruksi yang akan dijalankan oleh fungsi.
* **Function Return**: Pernyataan `return` yang mengembalikan nilai hasil eksekusi fungsi kepada pemanggilnya.

#### Struktur Rinci Function Header:
`def nama_fungsi(parameter1, parameter2):`

1.  **`def`**: *Keyword* wajib untuk memulai definisi fungsi.
2.  **`nama_fungsi`**: Nama yang Anda berikan untuk fungsi tersebut (contoh: `mencari_luas_persegi_panjang`).
3.  **`(parameter1, parameter2)`**: Parameter yang berfungsi sebagai "wadah" untuk nilai input yang akan digunakan di dalam fungsi.
4.  **`:` (titik dua)**: Penanda akhir dari *header* dan awal dari *function body*.

### Memanggil Fungsi

Setelah fungsi didefinisikan, ia tidak akan berjalan sampai Anda **memanggilnya**.

```python
# Hanya mendefinisikan, tidak ada output
def mencari_luas_persegi_panjang(panjang, lebar):
    luas_persegi_panjang = panjang * lebar
    return luas_persegi_panjang

# Memanggil fungsi tanpa menyimpan hasilnya
mencari_luas_persegi_panjang(10, 5) # Kode ini berjalan, tapi hasilnya tidak terlihat
```

Agar hasilnya bisa digunakan, kita perlu menyimpannya dalam sebuah variabel.

```python
# Memanggil fungsi dan menyimpan hasilnya
persegi_panjang_pertama = mencari_luas_persegi_panjang(5, 10)

# Menampilkan hasil yang sudah disimpan
print(persegi_panjang_pertama)
```

**Output:**
```
50
```

### Docstring: Dokumentasi Fungsi Anda

Untuk membuat fungsi lebih mudah dipahami, gunakan **docstring** (*documentation string*). Ini adalah string multi-baris tepat di bawah *header* fungsi untuk menjelaskan tujuannya, argumennya, dan apa yang dikembalikannya.

```python
def mencari_luas_persegi_panjang(panjang, lebar):
    """
    Fungsi ini digunakan untuk menghitung luas persegi panjang.

    Args:
        panjang (int): Panjang dari persegi panjang.
        lebar (int): Lebar dari persegi panjang.

    Returns:
        int: Luas persegi panjang hasil perhitungan.
    """
    luas_persegi_panjang = panjang * lebar
    return luas_persegi_panjang

persegi_panjang_pertama = mencari_luas_persegi_panjang(5, 10)
print(persegi_panjang_pertama)
```

---

## Argumen dan Parameter

Sering tertukar, tetapi keduanya berbeda.
* **Parameter**: Variabel yang ada di dalam tanda kurung pada definisi fungsi (contoh: `panjang` dan `lebar`).
* **Argumen**: Nilai aktual yang Anda berikan saat memanggil fungsi (contoh: `5` dan `10`).

```python
def fungsi_saya(a, b, c): # a, b, c adalah parameter
    # function body

fungsi_saya(1, 50, 'Dicoding') # 1, 50, 'Dicoding' adalah argumen
```

### 1. Argumen

Ada dua jenis utama argumen di Python:

#### a. Keyword Argument
Argumen yang didahului oleh nama parameternya secara eksplisit. Kelebihannya, urutan tidak menjadi masalah.

```python
def mencari_luas_persegi_panjang(panjang, lebar):
    return panjang * lebar

# Urutan tidak penting karena nama parameter disebutkan
hasil = mencari_luas_persegi_panjang(lebar=10, panjang=5)
print(hasil)
```

**Output:**
```
50
```

#### b. Positional Argument
Argumen yang nilainya diberikan berdasarkan posisi atau urutan parameternya. Anda tidak menyebutkan nama parameter.

```python
def mencari_luas_persegi_panjang(panjang, lebar):
    return panjang * lebar

# 5 akan masuk ke 'panjang', 10 akan masuk ke 'lebar'
hasil = mencari_luas_persegi_panjang(5, 10)
print(hasil)
```

### 2. Parameter

Python menyediakan 5 jenis parameter untuk kontrol yang lebih fleksibel.

#### 1. Positional-or-Keyword (Default)
Parameter standar yang bisa menerima argumen posisi maupun *keyword*.

```python
def greeting(nama, pesan):
    return "Halo, " + nama + "! " + pesan

print(greeting("Dicoding", "Selamat pagi!")) # Positional
print(greeting(pesan="Selamat sore!", nama="Dicoding")) # Keyword
```

**Output:**
```
Halo, Dicoding! Selamat pagi!
Halo, Dicoding! Selamat sore!
```

#### 2. Positional-Only
Parameter yang hanya bisa menerima argumen posisi. Ditandai dengan `/` setelah daftar parameter.

```python
def penjumlahan(a, b, /):
    return a + b

print(penjumlahan(8, 50)) # Benar

# print(penjumlahan(a=8, b=50)) # Ini akan menghasilkan TypeError
```

#### 3. Keyword-Only
Parameter yang hanya bisa menerima *keyword argument*. Ditandai dengan `*` sebelum daftar parameter.

```python
def greeting(*, nama, pesan):
    return "Halo, " + nama + "! " + pesan

print(greeting(pesan="Selamat sore!", nama="Dicoding")) # Benar

# print(greeting("Dicoding", "Selamat sore!")) # Ini akan menghasilkan TypeError
```

#### 4. Var-Positional (`*args`)
Parameter yang bisa menampung sejumlah argumen posisi yang bervariasi. Argumen-argumen ini akan dikumpulkan ke dalam sebuah **tuple**.

```python
def hitung_total(*args):
    print(f"Tipe data args: {type(args)}")
    total = sum(args)
    return total

print(hitung_total(1, 2, 3, 4, 5))
```

**Output:**
```
Tipe data args: <class 'tuple'>
15
```

#### 5. Var-Keyword (`**kwargs`)
Parameter yang bisa menampung sejumlah *keyword argument* yang bervariasi. Argumen-argumen ini akan dikumpulkan ke dalam sebuah **dictionary**.

```python
def cetak_info(**kwargs):
    print(f"Tipe data kwargs: {type(kwargs)}")
    info = ""
    for key, value in kwargs.items():
        info += f"{key}: {value}, "
    return info

print(cetak_info(nama="Dicoding", usia="8", pekerjaan="Platform Edukasi"))
```

**Output:**
```
Tipe data kwargs: <class 'dict'>
nama: Dicoding, usia: 8, pekerjaan: Platform Edukasi, 
```

---

## Fungsi Anonim (Lambda Expression)

Terkadang, Anda butuh fungsi sederhana yang hanya digunakan sekali. Daripada menggunakan `def`, Anda bisa membuat **fungsi anonim** dengan *lambda expression*. Ini adalah fungsi satu baris tanpa nama.

Struktur: `lambda parameter: ekspresi`

```python
# Fungsi biasa
def penjumlahan(a, b):
    return a + b

# Versi lambda
penjumlahan_lambda = lambda a, b: a + b

print(penjumlahan_lambda(10, 20)) # Output: 30
```

Contoh lain:
```python
mencari_luas_persegi_panjang = lambda panjang, lebar: panjang * lebar
print(mencari_luas_persegi_panjang(5, 10)) # Output: 50
```

Sebuah fungsi lambda dapat menerima argumen dalam jumlah berapa pun, tetapi hanya bisa memiliki **satu ekspresi** (satu operasi).

---

## Scope Variabel: Global dan Lokal

*Scope* adalah wilayah di dalam program tempat sebuah variabel dapat diakses.

### 1. Variabel Global
Variabel yang didefinisikan di luar fungsi mana pun. Ia dapat diakses dari seluruh bagian program.

```python
a = 10  # Variabel global

def tambah(b):
    # Variabel 'a' dapat diakses dari dalam fungsi
    result = a + b
    return result

bilangan_pertama = tambah(20)
print(bilangan_pertama) # Output: 30
```

### 2. Variabel Lokal
Variabel yang didefinisikan di dalam sebuah fungsi. Ia hanya dapat diakses dari dalam fungsi tersebut.

```python
def add(a, b):
    lokal_var = 5  # Variabel lokal
    result = a + b - lokal_var
    return result

bilangan_pertama = add(10, 20)
print(bilangan_pertama) # Output: 25

# print(lokal_var) # Ini akan menghasilkan NameError karena di luar scope
```

---

## Menulis Modul pada Python

Setiap file Python (`.py`) adalah sebuah modul. Anda bisa mengimpor fungsi, kelas, atau variabel dari satu file ke file lainnya.

Misalkan Anda memiliki dua file dalam satu direktori:

**File 1: `hello.py`**
```python
def mencari_luas_persegi_panjang(panjang, lebar):
    luas_persegi_panjang = panjang * lebar
    return luas_persegi_panjang

nama = "Dicoding Indonesia"
```

**File 2: `main.py`**
```python
# Cara 1: Mengimpor seluruh modul
import hello

persegi_panjang_pertama = hello.mencari_luas_persegi_panjang(5, 10)
print(persegi_panjang_pertama)
print(hello.nama)
```

**Output:**
```
50
Dicoding Indonesia
```

Anda juga bisa mengimpor bagian spesifik untuk menghindari pengetikan nama modul berulang kali.

**File 2: `main.py` (Cara 2)**
```python
# Cara 2: Mengimpor fungsi dan variabel secara spesifik
from hello import mencari_luas_persegi_panjang, nama

persegi_panjang_pertama = mencari_luas_persegi_panjang(5, 10)
print(persegi_panjang_pertama)
print(nama)
```

**Output:**
```
50
Dicoding Indonesia
```
---

## Prosedur

Seperti yang dibahas sebelumnya, **prosedur** adalah subprogram yang menjalankan serangkaian instruksi tetapi **tidak mengembalikan nilai**. Dalam Python, ini sama dengan fungsi yang tidak memiliki pernyataan `return` atau memiliki `return` tanpa nilai apa pun setelahnya.

```python
# Ini adalah sebuah prosedur
def greeting(name):
    print("Halo " + name + ", Selamat Datang!")

# Memanggil prosedur
greeting("Dicoding Indonesia")
```

**Output:**
```
Halo Dicoding Indonesia, Selamat Datang!
```

Perhatikan bahwa prosedur ini langsung menjalankan aksi (`print`) di dalamnya, bukan mengembalikan nilai untuk diproses lebih lanjut.

Kita juga bisa membuat prosedur tanpa parameter:
```python
def sapa_dunia():
    print("Halo Dunia, Selamat Datang!")

sapa_dunia()
```

**Output:**
```
Halo Dunia, Selamat Datang!

Sekian dari Section ini, semoga membantu!!