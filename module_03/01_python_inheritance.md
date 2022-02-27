# Konsep Pewarisan

Coba anda perhatikan ketiga kelas `Kucing`, `Anjing`, dan `Burung` berikut.

```Python
class Kucing:
    def __init__(self, nama, umur, bisa_terbang, heterochromia):
        self.nama = nama
        self.umur = umur
        self.bisa_terbang = bisa_terbang
        self.heterochromia = heterochromia

    def tambah_umur(self):
        self.umur += 1

class Anjing:
    def __init__(self, nama, umur, bisa_terbang):
        self.nama = nama
        self.umur = umur
        self.bisa_terbang = bisa_terbang

    def tambah_umur(self):
        self.umur += 1

class Burung:
    def __init__(self, nama, umur, bisa_terbang, warna):
        self.nama = nama
        self.umur = umur
        self.bisa_terbang = bisa_terbang
        self.warna = warna

    def tambah_umur(self):
        self.umur += 1
```

Anda dapat melihat bahwa ada beberapa kesamaan atribut antara ketiga kelas tersebut. Dalam OOP, kita dapat memanfaatkan konsep pewarisan jika kita dapat mendefinisikan kesamaan antara objek yang satu dengan objek lainnya.

Ketiga kelas diatas dapat didefinisikan sebagai turunan dari kelas `Hewan`.

```Python
class Hewan:
    def __init__(self, nama, umur, bisa_terbang):
        self.nama = nama
        self.umur = umur
        self.bisa_terbang = bisa_terbang

    def tambah_umur(self):
        self.umur += 1

# Kucing merupakan subclass dari Hewan
class Kucing(Hewan):
    def __init__(self, nama, umur, bisa_terbang, heterochromia):
        super().__init__(nama, umur, bisa_terbang)
        self.heterochromia = heterochromia

# Anjing merupakan subclass dari Hewan
class Anjing(Hewan):
    def __init__(self, nama, umur, bisa_terbang):
        super().__init__(nama, umur, bisa_terbang)

# Burung merupakan subclass dari Hewan
class Burung(Hewan):
    def __init__(self, nama, umur, bisa_terbang, warna):
        super().__init__(nama, umur, bisa_terbang)
        self.warna = warna
```

Kelas `Hewan` merupakan ***superclass*** dari kelas `Kucing`, `Anjing`, dan `Burung`. Kita menyebut `Kucing`, `Anjing`, dan `Burung` sebagai ***subclass*** dari kelas `Hewan` yang mewarisi properti atribut dan fungsi pada kelas `Hewan`. Perhatikan bahwa atribut dan fungsi yang sama (atau serupa) pada ***subclass*** atau ***child-class*** didefinisikan pada kelas `Hewan` sebagai ***superclass*** atau ***parent-class***.

Perhatikan potongan kode sebelumnya, untuk menerapkan prinsip pewarisan dalam bahasa pemrograman Python, kita menambahkan parameter nama ***parent-class*** sebagai argumen penanda kelas.

```Python
class Kucing(Hewan):
    # konstruktor dan fungsi
    ...
    ...

class Child(Parent):
    # konstruktor dan fungsi
    ...
    ...
```

Implementasi konstruktor pada subclass juga harus disesuaikan untuk menerapkan konsep pewarisan. Ekspresi `super().__init__(...)` menyatakan bahwa saat membuat objek (misalnya `Kucing`) terlebih dahulu memanggil konstruktor ***parent-class*** (dalam hal ini kelas `Hewan`). Dalam OOP, kata kunci `super` merujuk pada ***parent-class***, baik itu merupakan konstruktor ataupun juga method/fungsi yang ada pada *parent-class*. Selain menggunakan kata kunci `super()`, kita juga dapat memanggil konstruktor dari *parent-class* dengan menggunakan format `ParentClassName.__init__(arg1, arg2, ...)`.

```Python
h = Hewan("Hewan", 6, True)
print(h.nama)       # Hewan

kitty = Kucing("Kitty", 3, False, True)
print(kitty.umur)   # 3

doggy = Anjing("Doggy", 2, False)
print(doggy.umur)   # 2

birdie = Burung("Birdie", 1, True, "Oranye")
print(birdie.umur)  # 1
```

Berdasarkan prinsip pewarisan, *child-class* mewarisi seluruh atribut dan fungsi yang bersifat publik dari *parent-class*. Contoh berdasarkan kode yang sudah dibuat sebelumnya, fungsi `tambah_umur()` yang didefinisikan dalam kelas `Hewan` dapat diakses dari objek `Kucing` yang merupakan turunan dari kelas `Hewan`.

```Python
kitty = Kucing("Kitty", 3, False, True)

kitty.tambah_umur() # umur kitty bertambah dari 3 menjadi 4

# Mencetak 'Kitty bertambah tua! Umur Kitty sekarang 4 tahun.'
print("{:s} bertambah tua! Umur {:s} sekarang {:d} tahun.".format(kitty.nama, kitty.nama, kitty.umur)) 
```

## Apakah *child-class* boleh memiliki fungsi tambahan yang tidak terdapat pada *parent-class*?

Jawabannya tentu saja boleh! Anggap saja bahwa dalam PBO kelas anak akan mewarisi semua ciri dan perilaku orang-tuanya. Namun, anak juga bisa mempunyai ciri dan bakat tambahan lainnya yang tidak dimiliki oleh orang-tuanya. Contoh:

```Python
class BentukSegiEmpat:
    def __init__(self, a, b, c, d):
        self.sisi_1 = a
        self.sisi_2 = b
        self.sisi_3 = c
        self.sisi_4 = d
    
    def get_keliling(self):
        return self.sisi_1 + self.sisi_2 + self.sisi_3 + self.sisi_4

class PersegiPanjang(BentukSegiEmpat):
    def __init__(self, a, b):
        super().__init__(a, b, a, b)

    # menghitung luas persegi panjang
    def get_luas(self):
        return self.sisi_1 * self.sisi_2

class Persegi(PersegiPanjang):
    def __init__(self, a):
        super().__init__(a, a)
    
    # menghitung luas persegi
    def get_luas(self):
        return self.sisi_1 ** 2

persegi_1 = Persegi(3)
print(persegi_1.get_luas())     # 9
print(persegi_1.get_keliling()) # 12
```

## Eksperimen menarik

Apa jadinya jika pada konstruktor *child-class* tidak memanggil konstruktor *parent-class* dengan kata kunci `super()`?

Perhatikan kode yang ditulis dalam eksperimen berikut:

```Python
class Hewan:
    def __init__(self, nama, umur, bisa_terbang):
        self.nama = nama
        self.umur = umur
        self.bisa_terbang = bisa_terbang
    
    def tambah_umur(self):
        self.umur += 1

class Kucing(Hewan):
    pass
```

Ternyata kita dapat membuat objek `Kucing` dengan atribut `nama`, `umur`, `bisa_terbang` tanpa perlu mendefinisikan konstruktor dalam kelas `Kucing`.

```Python
kitty = Kucing("Kitty", 4, False)
kitty.tambah_umur()
print(kitty.umur)   # 5
```

Ternyata kita dapat membuat objek `Kucing` dengan atribut yang diharapkan. Perhatikan bahwa untuk proses instansiasi objek, kita perlu menspesifikasikan semua atribut yang ada pada *parent-class* yaitu `Kitty(nama, umur, bisa_terbang)` meskipun secara eksplisit kita tidak menulis implementasinya pada kelas `Kucing`. Sesuai konsep pewarisan, fungsi `tambah_umur()` dapat diakses pada objek `kitty`.

Lalu apa jadinya kalau kita tidak menspesifikasikan atribut pada konstruktor `Kucing` seperti berikut ini? Ini tentu akan menghasilkan pesan kesalahan.

```Python
kitty = Kucing()        # Tidak bisa membuat objek: ERROR konstruktor
```

Anda bisa mencoba sendiri untuk eksperimen lainnya. Contoh nya seperti berikut ini. Apa jadinya kalau kita mendefinisikan konstruktor di kelas kucing seperti berikut ini?

```Python
class Kucing(Hewan):
    def __init__(self):
        pass

kitty = Kucing()
```

atau kondisi berikut

```Python
class Kucing(Hewan):
    def __init__(self, nama, umur, bisa_terbang):
        pass

kitty = Kucing("Kitty", 4, False)
```

Apa yang dapat anda simpulkan?
