# Enkapsulasi dan Abstraksi dalam Python

Penerapan enkapsulasi sebenarnya secara tidak langsung telah dibahas pada materi tentang [kelas dan objek](01_python_class_and_object.md). Dalam mendefinisikan sebuah kelas, kita menerapkan konsep enkapsulasi. Konsep enkapsulasi merujuk kepada menyatukan atribut-atribut dan fungsi-fungsi terkait sebuah data kedalam satu unit yang dinamakan kelas.

Berikut merupakan contoh implementasi kelas `Kalender`:

```Python
class Kalender:
    def __init__(self, int: tanggal, int: bulan, int: tahun):
        self.tanggal = tanggal
        self.bulan = bulan
        self.tahun = tahun

    def get_nama_bulan(self) -> str:
        nama_bulan = ["Jan", "Feb", "Mar", "Apr", "Mei", "Jun",
                      "Jul", "Agt", "Sep", "Okt", "Nov", "Des"]
        # get nama bulan, ingat indexing dimulai dari 0
        return nama_bulan[self.bulan-1]

    def to_string(self) -> str:
        return "{:02d} / {:02d} / {:d}".format(self.tanggal, self.bulan, self.tahun)

tgl_sekarang = Kalender(19, 2, 2022)
print(tgl_sekarang.get_nama_bulan())    # Feb
print(tgl_sekarang.to_string())         # 19 / 02 / 2022
```

Dalam membuat kelas `Kalender` kita melakukan **enkapsulasi** terhadap atribut `tanggal`, `bulan`, `tahun` dan fungsi `get_nama_bulan`, `to_string` kedalam sebuah kelas yang merepresentasikan tanggal dalam sistem kalender masehi.

Kita juga menerapkan konsep abstraksi dalam fungsi `get_nama_bulan` dan `to_string`. Pada fungsi `get_nama_bulan`, kita menyembunyikan detail bagaimana cara konversi dari urutan bulan (`int`) menjadi `str` nama bulan yang sesuai. Kita yakin bahwa memanggil fungsi `get_nama_bulan` pada objek yang `tgl_sekarang` akan memgembalikan nama bulan dalam tipe data `str`. Begitu pula dengan fungsi `to_string`, kita yakin bahwa dengan memanggil fungsi tersebut akan mendapatkan format penulisan tanggal dalam tipe data `str`. Dengan konsep abstraksi ini, kita dapat menggunakan bagian program lain dalam aplikasi yang telah kita buat (prinsip *reusable*) tanpa perlu kembali mendefinisikan kembali program yang serupa.

## Hak akses variabel dan fungsi dalam Python

Secara default, saat atribut kelas maupun atribut objek diberi assignment, atribut tersebut akan bersifat `public`. Atribut yang bersifat `public` dapat diakses oleh objek lainnya secara langsung.

```Python
class Kalender:
    def __init__(self, int: tanggal, int: bulan, int: tahun):
        self.tanggal = tanggal
        self.bulan = bulan
        self.tahun = tahun
    
    def get_nama_bulan(self) -> str:
        nama_bulan = ["Jan", "Feb", "Mar", "Apr", "Mei", "Jun",
                      "Jul", "Agt", "Sep", "Okt", "Nov", "Des"]
        # get nama bulan, ingat indexing dimulai dari 0
        return nama_bulan[self.bulan-1]

    def to_string(self) -> str:
        return "{:02d} / {:02d} / {:d}".format(self.tanggal, self.bulan, self.tahun)

tgl_sekarang = Kalender(19, 2, 2022)
print(tgl_sekarang.get_nama_bulan())    # 'Feb'
print(tgl_sekarang.bulan)               # 2
```

Lain halnya dengan atribut yang bersifat `public`, atribut yang bersifat `private` tidak dapat diakses dari objek lain. Dalam bahasa pemrograman Python atribut atau fungsi yang bersifat `private` dicirikan dengan tanda ***double-underscore*** (`__nama_variabel`) diawal nama atribut maupun fungsi. Berikut merupakan contoh implementasi atribut `private` pada properti `__bulan`:

```Python
class Kalender:
    def __init__(self, int: tanggal, int: bulan, int: tahun):
        self.tanggal = tanggal
        self.__bulan = bulan
        self.tahun = tahun
    
    def get_nama_bulan(self) -> str:
        nama_bulan = ["Jan", "Feb", "Mar", "Apr", "Mei", "Jun",
                      "Jul", "Agt", "Sep", "Okt", "Nov", "Des"]
        # variabel __bulan dapat diakses dari objek itu sendiri
        return nama_bulan[self.__bulan-1]

    def to_string(self) -> str:
        return "{:02d} / {:02d} / {:d}".format(self.tanggal, self.__bulan, self.tahun)

tgl_sekarang = Kalender(19, 2, 2022)
print(tgl_sekarang.get_nama_bulan())    # 'Feb'
print(tgl_sekarang.__bulan)             # ERROR akses properti private
```

## Fungsi `getter` dan `setter` untuk mengakses properti `private`

Kita dapat membuat fungsi `getter` dan `setter` untuk mengakses variabel yang bersifat `private`. Dengan begitu, secara tidak langsung fungsi `getter` dan `setter` harus bersifat `public`.

```Python
class Kalender:
    def __init__(self, int: tanggal, int: bulan, int: tahun):
        self.tanggal = tanggal
        self.__bulan = bulan
        self.__tahun = tahun
    
    # contoh fungsi `getter`
    def get_bulan(self) -> int:
        return self.__bulan

    # contoh fungsi `setter`
    def set_tahun(self, tahun_baru):
        self.__tahun = tahun_baru

    def to_string(self) -> str:
        return "{:02d} / {:02d} / {:d}".format(self.tanggal, self.__bulan, self.__tahun)

tgl_sekarang = Kalender(19, 2, 2022)
print(tgl_sekarang.get_bulan())     # 2
print(tgl_sekarang.setTahun(2023))
print(tgl_sekarang.to_string())     # 19 / 02 / 2023
```

## Materi Ekstra: membandingkan kesamaan antara dua objek

Untuk tipe data dasar seperti int, double, str, kita dapat melakukan perbandingan kesamaan antara dua data dengan operator `==`.

```Python
a = 7
b = 7

a == b      # True

# Bandingkan dua objek tanggal yang atributnya sama
tgl_ini = Kalender(19, 2, 2022)
tgl_itu = Kalender(19, 2, 2022)

tgl_ini == tgl_itu      # False
```

Bagaimana jika kita ingin membandingkan kesamaaan antara dua objek (yang kita definisikan)? Kita dapat mendefinisikan kembali fungsi `__eq__()` pada kelas yang akan kita bandingkan.

```Python
class Kalender:
    def __init__(self, int: tanggal, int: bulan, int: tahun):
        self.tanggal = tanggal
        self.bulan = bulan
        self.tahun = tahun
    
    def __eq__(self, obj2):
        # ERROR objek yang dibandingkan bukan dari kelas yang sama
        if not isinstance(obj2, Kalender):
            return NotImplemented 
        return  self.tanggal == obj2.tanggal and 
                self.bulan == obj2.bulan and 
                self.tahun == obj2.tahun

tgl_ini = Kalender(19, 2, 2022)
tgl_itu = Kalender(19, 2, 2022)

tgl_ini == tgl_itu      # True
```
