# Python Abstract Base Class

Sebelumnya pada materi [enkapsulasi](../module_02/03_python_encapsulation_abstraction.md) kita sudah pernah membahas mengenai abstraksi data. Secara umum, konsep abstraksi ini tidak hanya dapat diterapkan untuk melakukan abstraksi data. Kali ini kita akan membahas konsep abstraksi di tingkat kelas dan objek.

Konsep abstraksi dalam OOP dalam bahasa pemrograman Java dan C++ dapat dimungkinkan dengan adanya kelas yang bersifat abstrak. Dalam bahasa pemrograman Java, kelas abstrak merupakan kelas yang tidak dapat dibuat objeknya. Dalam bahasa pemrograman Python, kita juga dapat melakukan hal yang serupa dengan mewarisi kelas **ABC (*Abstract Base Class*)**.

Coba perhatikan kode berikut ini:

```Python
import math

class PersegiPanjang:
    def __init__(self, panjang, lebar):
        self.panjang = panjang
        self.lebar = lebar

    def get_luas(self):
        return self.panjang * self.lebar

    def get_keliling(self):
        return 2 * (self.panjang + self.lebar)

class SegitigaSikuSiku:
    def __init__(self, alas, tinggi):
        self.alas = alas
        self.tinggi = tinggi
        self.sisi_miring = math.sqrt(alas**2 + tinggi**2)

    def get_luas(self):
        return 0.5 * self.alas * self.tinggi

    def get_keliling(self):
        return self.alas + self.tinggi + self.sisi_miring

class Lingkaran:
    def __init__(self, jari_jari):
        self.jari_jari = jari_jari

    def get_luas(self):
        return math.pi*jari_jari**2

    def get_keliling(self):
        return 2*math.pi*jari_jari
```

Kita dapat melihat bahwa pada program tersebut, ketiga kelas memiliki kesamaan bahwa ketiganya memiliki fungsi `get_luas()` dan `get_keliling()`. Bila kita mengingat kembali materi mengenai [pewarisan](../module_03/01_python_inheritance.md), kita dapat membuat *parent-class* dengan nama `Bentuk2D`. Namun, anda dapat memperhatikan pula bahwa *parent-class* ini tidak perlu dibuat objeknya karena sangat sulit melakukan implementasi fungsi `get_luas()` dan `get_keliling()` pada kelas `Bentuk2D`. Karena karakteristik inilah kita dapat menentukan bahwa konsep `Bentuk2D` merupakan konsep abstrak dimana setiap `Bentuk2D` dapat dihitung luas (`get_luas()`) dan kelilingnya (`get_keliling()`). Konsep abstrak ini dapat diimplementasikan dalam Python dengan mewarisi kelas `ABC` (***Abstract Base Class***) dan menggunakan dekorator `@abstractmethod` untuk menandakan bahwa fungsi yang ada pada kelas abstrak wajib diimplementasikan oleh semua kelas yang akan mewarisinya. Coba perhatikan kode berikut yang merupakan contoh penerapan konsep abstraksi pada Python dengan mewarisi kelas `ABC`.

```Python
from abc import ABC, abstractmethod

# kelas Bentuk2D merupakan kelas abstrak dan tidak bisa diinstansiasi
class Bentuk2D(ABC):
    @abstractmethod
    def get_luas(self):
        # fungsi ini wajib diimplementasikan pada child-class
        pass
    
    @abstractmethod
    def get_keliling(self):
        # fungsi ini wajib diimplementasikan pada child-class
        pass

class PersegiPanjang(Bentuk2D):
    pass

class SegitigaSikuSiku(Bentuk2D):
    pass

class Lingkaran(Bentuk2D):
    pass
```

Kelas abstrak tidak dapat dibuat objeknya atau tidak dapat diinstansiasi.

```console
>> bentuk = Bentuk2D()
Traceback (most recent call last):
  File "/home/iwawiwi/code/Python/abstract_class/geometry_driver.py", line 3, in <module>
    bentuk = Bentuk2D()
TypeError: Can't instantiate abstract class Bentuk2D with abstract methods get_keliling, get_luas
```

Semua kelas yang mewarisi kelas abstrak tertentu wajib untuk membuat implementasi fungsi-fungsi abstrak yang didefinisikan pada kelas abstrak.

```console
>> persegi_panjang = PersegiPanjang(2, 4)
Traceback (most recent call last):
  File "/home/iwawiwi/code/Python/abstract_class/geometry_driver.py", line 4, in <module>
    persegi_panjang = PersegiPanjang(2, 4)
TypeError: Can't instantiate abstract class PersegiPanjang with abstract methods get_keliling, get_luas
```

Untuk memperbaiki pesan kesalahan yang muncul, kita wajib mengimplementasikan seluruh fungsi yang ditandai dengan dekorator `@abstractmethod`.

```Python
from abc import ABC, abstractmethod
import math

# kelas Bentuk2D merupakan kelas abstrak dan tidak bisa diinstansiasi
class Bentuk2D(ABC):
    @abstractmethod
    def get_luas(self):
        # fungsi ini wajib diimplementasikan pada child-class
        pass
    
    @abstractmethod
    def get_keliling(self):
        # fungsi ini wajib diimplementasikan pada child-class
        pass

class PersegiPanjang(Bentuk2D):
    def __init__(self, panjang, lebar):
        self.panjang = panjang
        self.lebar = lebar

    def get_luas(self):
        return self.panjang * self.lebar

    def get_keliling(self):
        return 2 * (self.panjang + self.lebar)

class SegitigaSikuSiku(Bentuk2D):
    def __init__(self, alas, tinggi):
        self.alas = alas
        self.tinggi = tinggi
        self.sisi_miring = math.sqrt(alas**2 + tinggi**2)

    def get_luas(self):
        return 0.5 * self.alas * self.tinggi

    def get_keliling(self):
        return self.alas + self.tinggi + self.sisi_miring

class Lingkaran(Bentuk2D):
    def __init__(self, jari_jari):
        self.jari_jari = jari_jari

    def get_luas(self):
        return math.pi * self.jari_jari**2

    def get_keliling(self):
        return 2 * math.pi * self.jari_jari
```
