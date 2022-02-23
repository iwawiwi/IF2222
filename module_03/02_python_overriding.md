# Konsep Overriding

Perhatikan definisi kelas `Hewan`, `Kucing`, dan `Anjing` dan program berikut berikut ini.

```Python
class Hewan:
    def __init__(self, nama, umur, bisa_terbang):
        self.nama = nama
        self.umur = umur
        self.bisa_terbang = bisa_terbang

    def tambah_umur(self):
        self.umur += 1

    def to_string(self):
        bisa = "bisa" if self.bisa_terbang else "tidak bisa"
        return "{:s} berumur {:d} {:s} terbang".format(self.nama, self.age, bisa)


class Kucing(Hewan):
    def __init__(self, nama, umur, bisa_terbang, heterochromia):
        super.__init__(nama, umur, bisa_terbang)
        self.heterochromia = heterochromia


class Anjing:
    def __init__(self, nama, umur, bisa_terbang):
        self.nama = nama
        self.umur = umur
        self.bisa_terbang = bisa_terbang

    # Override fungsi
    def to_string(self):
        return "{s:nama} menggonggong!"



kitty = Kucing("Kitty", 2, False)
# print: 'Kitty berumur 2 tidak bisa terbang' 
print(kitty.to_string())
doggy = Anjing("Doggy", 3, False)
# print: 'Doggy menggonggong'
print(doggy.to_string())
```

Perhatikan bahwa fungsi `to_string()` dalam kelas `Anjing` didefinisikan kembali sebagai `nama_anjing menggonggong!`. Kita melakukan ***overriding*** fungsi `to_string()` dari kelas `Hewan` dan mendefinisikan kembali pada kelas `Anjing`. Ketika objek `doggy` memanggil fungsi `to_string()`, itu sama artinya dengan memanggil implementasi fungsi `to_string` yang telah didefinisikan kembali pada kelas `Anjing`.
