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

Implementasi konstruktor pada subclass juga harus disesuaikan untuk menerapkan konsep pewarisan. Ekspresi `super().__init__(...)` menyatakan bahwa saat membuat objek (misalnya `Kucing`) terlebih dahulu memanggil konstruktor ***parent-class*** (dalam hal ini kelas `Hewan`). Dalam OOP, kata kunci `super` merujuk pada ***parent-class***, baik itu merupakan konstruktor ataupun juga method/fungsi yang ada pada *parent-class*.

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

## Materi Tambahan

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
