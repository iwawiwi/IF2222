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
        super.__init__(nama, umur, bisa_terbang)
        self.heterochromia = heterochromia

# Anjing merupakan subclass dari Hewan
class Anjing(Hewan):
    def __init__(self, nama, umur, bisa_terbang):
        super.__init__(nama, umur, bisa_terbang)

# Burung merupakan subclass dari Hewan
class Burung(Hewan):
    def __init__(self, nama, umur, bisa_terbang, warna):
        super.__init__(nama, umur, bisa_terbang)
        self.warna = warna
```

Kelas `Hewan` merupakan ***superclass*** dari kelas `Kucing`, `Anjing`, dan `Burung`. Kita menyebut `Kucing`, `Anjing`, dan `Burung` sebagai ***subclass*** dari kelas `Hewan` yang mewarisi properti atribut dan fungsi pada kelas `Hewan`. Perhatikan bahwa atribut dan fungsi yang sama (atau serupa) pada ***subclass*** atau ***child-class*** didefinisikan pada kelas `Hewan` sebagai ***superclass*** atau ***parent-class***.

Perhatikan potongan kode sebelumnya, untuk menerapkan prinsip pewarisan dalam bahasa pemrograman Python, kita menambahkan parameter nama ***parent-class*** sebagai argumen penanda kelas.

```Python
class Kucing(Hewan):
    # konstruktor dan method
```

Implementasi konstruktor pada subclass juga harus disesuaikan untuk menerapkan konsep pewarisan. Ekspresi `super.__init__(...)` menyatakan bahwa saat membuat objek (misalnya `Kucing`) terlebih dahulu memanggil konstruktor ***parent-class*** (dalam hal ini kelas `Hewan`). Dalam OOP, kata kunci `super` biasanya merujuk pada ***parent-class***.

```Python
h = Hewan("Hewan", 6, True)
print(h.nama)

kitty = Kucing("Kitty", 3, False, True)
print(kitty.umur)

doggy = Anjing("Doggy", 2, False)
print(doggy.umur)

birdie = Burung("Birdie", 1, True, "Oranye")
print(birdie.umur)
```
