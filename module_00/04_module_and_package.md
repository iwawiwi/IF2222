# Python Module

Modul dalam Python dapat berisi kumpulan variabel, fungsi, dan kelas. Python memiliki [modul bawaan](https://docs.python.org/3/py-modindex.html) yang dapat digunakan kembali pada program yang kita buat. Programmer juga dapat menspesifikasikan sendiri modul dengan membuat file berekstensi `*.py`. Modul diaktifkan dengan menggunakan kata kunci `import`. Nama modul yang di-import dapat diberikan alias. Kita juga dapat melakukan import beberapa variabel, fungsi, atau kelas (tidak semuanya) dalam modul dengan menggunakan kata kunci `from`

```Python
# import semua kelas, fungsi, dan atribut yang ada pada modul `math`
import math
# menjalankan fungsi sin dari modul `math`
# konstanta pi didapat dari modul `math`
x = math.sin(0.5*math.pi)       # x = 1.0 -> nilai dari sin dari 1/2 * pi-radian (atau sin 90 derajat)

# alternatif lain
import math as m
# perhatikan bahwa modul `math` dapat ditulis sebagai `m`
y = m.sin(0.5*m.pi)

# import fungsi sin, cos, dan tan dari modul `math`
from math import sin, cos, tan, pi
# dengan kata kunci `from`, kita dapat import fungsi tanpa perlu menuliskan nama modulnya
z = sin(0.5*pi)
```

## Import absolut

Dalam Python, import modul secara absolut dapat dilakukan dengan menuliskan secara lengkap lokasi modul dalam proyek, termasuk menuliskan **nama paket** (sub_folder) dan **nama modul** yang akan akan di-**import**. Secara default, interpreter Python akan mencari modul yang ada dalam daftar lokasi pencarian modul dengan kriteria sebagai berikut:

- Direktori kerja (atau lokasi main program) saat ini;
- Direktori yang terdaftar pada variabel PYTHONPATH pada lingkungan sistem operasi; dan
- Direktori terkait saat proses instalasi dan konfigurasi Python pertama kali. 
(Sumber: [RealPython](https://realpython.com/python-modules-packages/#the-module-search-path) gunakan mode privasi untuk akses halaman tak terbatas)

Cara melihat daftar lokasi pencarian modul (**kecuali direktori kerja saat ini**):

```Python
import sys

print(sys.path)
```

Perhatikan dalam kode diatas bahwa kita dapat melakukan import modul `sys` secara langsung dikarenakan modul ini terdapat dalam daftar lokasi pencarian modul. Contoh luaran program diatas adalah sebagai berikut:

```Python
['', '/home/iwawiwi/miniconda3/lib/python39.zip', '/home/iwawiwi/miniconda3/lib/python3.9', '/home/iwawiwi/miniconda3/lib/python3.9/lib-dynload', '/home/iwawiwi/miniconda3/lib/python3.9/site-packages']
```

Kita akan mencoba membuat sebuah proyek baru yang lokasinya diluar dari daftar pencarian modul Python yaitu dengan lokasi `~/root_module` atau lengkapnya `/home/iwawiwi/root_module` (contoh saja). Perhatikan kondisi inisial struktur folder `root_module` berikut:

```bash
.
├── __init__.py
├── modul_a.py
├── paket_a
│   ├── __init__.py
│   └── modul_b.py
└── paket_b
    ├── __init__.py
    ├── modul_c.py
    └── paket_ba
        ├── __init__.py
        └── modul_d.py
```

Kemudian, kode pada `modul_a.py` adalah sebagai berikut:

```Python
class KelasA():
    def __init__(self, attr_a):
        self.attr_a = attr_a
    
    def get_attr_a(self):
        return self.attr_a
```

Selanjutnya kode pada `modul_b.py` adalah sebagai berikut:

```Python
def tambah(a, b):
    return a + b
```

Selanjutnya kode pada `modul_c.py` adalah sebagai berikut:

```Python
def KelasC():
    def __init__(self, attr_c):
        self.attr_c = attr_c

    def get_attr_c(self):
        return self.attr_c
```

dan yang terakhir, kode pada `modul_d.py` adalah sebagai berikut:

```Python
def kali(a, b):
    return a * b
```

Terdapat kasus dimana dalam folder `root` ditambahkan file `driver_a.py` sehingga struktur folder menjadi seperti berikut:

```bash
.
├── __init__.py
├── driver_a.py
├── modul_a.py
├── paket_a
│   ├── __init__.py
│   └── modul_b.py
└── paket_b
    ├── __init__.py
    ├── modul_c.py
    └── paket_ba
        ├── __init__.py
        └── modul_d.py
```

Pernyataan **import absolut** dilakukan dengan cara menuliskan secara lengkap lokasi modul dalam proyek, termasuk menuliskan **nama paket** (sub_folder) dan **nama modul** yang akan akan di-**import**.

```Python
# kode dalam file root_module/driver_a.py

import paket_a.modul_b as modul_b
import paket_b.paket_ba.modul_d as modul_d

x = modul_b.tambah(10,5)        # x = 10+5 = 15
print(x)

y = modul_d.kali(4,5)           # y = 4*5 = 20
print(y)
```

Perhatikan bahwa program tersebut dapat dijalankan tanpa menghasilkan pesan kesalahan pada interpreter Python. Meskipun folder proyek tidak termasuk dalam daftar direktori pencarian yang didefinisikan `sys.path`, kita tetap dapat melakukan import modul yang ada dalam proyek. Hal ini dikarenakan file `driver_a.py` berada pada direktori kerja saat ini, sehingga interpreter juga akan mencari modul yang ada pada direktori `root_module` dan sub-folder lain di dalamnya (`paket_a`, `paket_b`, `paket_ba`).

Namun, coba kita perhatikan kondisi lainnya dimana kita menambahkan file `driver_b.py` (dengan konten yang sama dengan file `driver_a.py`) pada sub-folder `paket_a` sehingga struktur flder menjadi seperti berikut ini:

```bash
.
├── __init__.py
├── driver_a.py
├── modul_a.py
├── paket_a
│   ├── __init__.py
│   ├── driver_b.py
│   └── modul_b.py
└── paket_b
    ├── __init__.py
    ├── modul_c.py
    └── paket_ba
        ├── __init__.py
        └── modul_d.py
```

```Python
# kode dalam file root_module/paket_a/driver_b.py

import paket_a.modul_b as modul_b
import paket_b.paket_ba.modul_d as modul_d

x = modul_b.tambah(10,5)        # x = 10+5 = 15
print(x)

y = modul_d.kali(4,5)           # y = 4*5 = 20
print(y)
```

Jika program `driver_b.py` dijalankan akan muncul pesan kesalahan (ERROR) bahwa modul `paket_a` tidak ditemukan. Lalu apa bedanya dengan kasus kita sebelumnya (file `driver_a.py`)?. Jelas saja kasus ini berbeda dengan yang sebelumnya. Hal ini disebabkan karena, interpreter Python gagal menemukan folder `paket_a` (dan juga nantinya error untuk sub-folder `paket_b`) dalam daftar pencarian lokasi modul di lokasi direktori kerja saat ini yaitu folder `paket_a`. Tidak ada modul ataupun sub-folder dengan nama `paket_a` dalam direktori kerja kita saat ini yaitu folder `paket_a`.

Sebenarnya kita dapat menyelesaikannya dengan menuliskan **import relatif** (akan dibahas selanjutnya). Namun, jika kita ingin menggunakan import absolut (**CATATAN:** disarankan menggunakan jenis **import absolut** dikarenakan lebih mudah), kita dapat menggunakan perintah berikut untuk menambahkan direktori utama proyek kita (`root_module`) kedalam daftar direktori pencarian modul pada file `driver_b.py` sehingga kode menjadi:

```Python
# kode dalam file root_module/paket_a/driver_b.py
import sys, os.path
sys.path.append(os.path.abspath('/home/iwawiwi/root_module')) # lokasi direktori utama proyek 

import paket_a.modul_b as modul_b
import paket_b.paket_ba.modul_d as modul_d

x = modul_b.tambah(10,5)        # x = 10+5 = 15
print(x)

y = modul_d.kali(4,5)           # y = 4*5 = 20
print(y)
```

Perintah `sys.path.append(os.path.abspath('/home/iwawiwi/root_module'))` menambahkan direktori `/home/iwawiwi/root_module` kedalam daftar lokasi pencarian modul.

## Import relatif

Pada kasus sebelumnya, perintah import absolut akan mencari modul yang akan di-import pada daftar lokasi pencarian modul yang dispesifikasikan maupun direktori kerja saat ini. Anda juga sudah melihat bahwa untuk kasus sebelumnya, kita perlu menambahkan daftar lokasi pencarian modul ini jika kita ingin menggunakan import absolut. Terkadang jika struktur proyek kita banyak terdapat sub-folder atau sub-paket, penulisan penyataan import absolut bisa sangat panjang!

Alternatif lainnya kita dapat memanfaatkan **import relatif**. Namun, anda perlu memperhatikan bahwa dalam menggunakan import relatif kita tidak dapat mengeksekusi secara langsung kelas yang berisi pernyataan import relatif. Hal ini yang perlu diperhatikan oleh programmer dalam melakukan **import relatif**.

Dalam contoh berikut ini kita menggunakan kasus yang sama seperti kasus yang terakhir pada bagian import absolut (`driver_b.py`) namun tidak menspesifikasikan penambahan lokasi pencarian modul. Kita menggunakan simbol dot (`.`) dibagian awal nama paket untuk menyatakan lokasi paket yang sama dengan file saat ini. Simbol titik dua kali (`..`) untuk menyatakan lokasi paket berada pada folder diatas file saat ini (*parent dir*). Kemudian Simbol titik tiga kali (`...`) menyatakan lokasi paket berada pada dua folder diatas file saat ini (*grandparent dir*). Implementasi kode dalam `driver_b.py` adalah sebagai berikut:

```Python
# kode dalam file root_module/paket_a/driver_b.py

import .modul_b as modul_b              # modul_b satu level dengan driver_b
import ..paket_ba.modul_d as modul_d    # letak modul_d relatif terhadap driver_b 

x = modul_b.tambah(10,5)        # x = 10+5 = 15
print(x)

y = modul_d.kali(4,5)           # y = 4*5 = 20
print(y)
```

Belum cukup sampai disini saja. Seperti yang sudah disampaikan bahwa kita tidak dapat menjalankan file `drive_b.py` secara langsung dari console jika kita mengeksekusi file `driver_b.py` ini. Kita harus membuat file dengan lokasi diluar folder proyek utama atau di lokasi `/home/iwawiwi`. Sehingga kita struktur folder untuk dapat mengeksekusi file `driver_b` adalah sebagai berikut:

```bash
.
├── driver_module.py
└── root_module
    ├── __init__.py
    ├── driver_a.py
    ├── modul_a.py
    ├── paket_a
    │   ├── __init__.py
    │   ├── driver_b.py
    │   └── modul_b.py
    └── paket_b
        ├── __init__.py
        ├── modul_c.py
        └── paket_ba
            ├── __init__.py
            └── modul_d.py
```

Perhatikan bahwa kita membuat file `driver_module.py` diluar folder `root_module`, dan didalam file `driver_module.py` ini kita akan mengeksekusi file `root_module/paket_a/driver_b.py` dengan menuliskan kode berikut:

```Python
import root_module.paket_a.driver_b
```

Referensi:

- [RealPython](https://realpython.com/python-modules-packages/)
- [GeeksForGeeks](https://www.geeksforgeeks.org/python-import-from-parent-directory/)
- [Stackoverflow](https://stackoverflow.com/questions/28897444/how-to-import-a-package-located-in-its-parent-directory-using-absolute-import-in)
- [Napuzba.com](https://napuzba.com/a/import-error-relative-no-parent)