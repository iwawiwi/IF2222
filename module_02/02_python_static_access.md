# Abstraksi Data dalam Python (1)

## Variabel dan fungsi static dalam Python

Dalam bahasa pemrograman yang mendukung OOP seperti Java dan Python, biasanya terdapat istilah atribut `static` dan fungsi `static`. Atribut yang bersifat `non-static` pada umumnya dapat memiliki nilai yang dapat berbeda antara objek satu dengan objek yang laiinya yang dibentuk dari satu kelas yang sama. Berbeda halnya dengan atribut dan fungsi yang bersifat `non-static`, atribut dan fungsi yang bersifat `static` dapat diakses secara bersama (*shared*) dari seluruh objek.

Dalam Python, variabel `static` sering disebut sebagai **atribut kelas**, sedangkan variabel `non-static` sering disebut sebagai **atribut objek**. Berikut ini merupakan implementasi variabel dan fungsi yang bersifat `static`.

```Python
class Bola:
    # variabel static
    jumlah_bola = 0

    def __init__(self, warna, jarijari):
        self.warna = warna
        self.jarijari = jarijari
        # cara akses variabel static dengan menulis nama kelasnya
        Bola.jumlah_bola += 1

    def get_volume(self):
        return (4 / 3) * 3.14 * (self.jarijari ** 3)
    
    # fungsi static tidak perlu argumen self
    def get_jumlah_bola():
        return Bola.jumlah_bola
```

Berdasarkan pemaparan sebelumnya, variabel `static` dapat diakses secara bersama.

```Python
bola1 = Bola("Merah", 4);
print(bola1.jumlah_bola)        # 1
# pemanggilan secara langsung dengan menggunakan nama kelas
print(Bola.get_jumlah_bola())   # 1

bola2 = Bola("Hijau", 3)
print(bola2.jumlah_bola)        # 2
print(Bola.get_jumlah_bola())   # 2

bola2.get_jumlah_bola()         # ERROR
```

Perhatikan ekspresi terakhir bahwa fungsi yang bersifat `static` tidak menggunakan argumen `self`. Ingat kembali bahwa dalam bahasa pemrograman Python, jika kita mengakses fungsi dari sebuah objek, secara implisit parameter pertama dari fungsi tersebut merupakan objek itu sendiri (`self`). Dalam fungsi `static` kita tidak perlu mendefinisikan parameter `self` pada argumen fungsi dikarenakan kita dapat mengakses fungsi tersebut dengan menggunakan nama kelas yang bersesuaian.

Jika kita ingin mengakses variabel `static` dengan menggunakan referensi objek, kita dapat menuliskan parameter `self` pada argumen fungsi, namun pada dasarnya hal ini sama saja dengan mendefinisikan fungsi dari sebuah objek dimana kondisi ini tidak tepat secara konsep OOP.

Pada implementasi dalam problem yang nyata, contoh penerapan deklarasi atribut static biasanya dilakukan untuk mebuat konstanta. Sebagai contoh:

```Python
class Bola:
    def __init__(self, warna, jarijari, material):
        self.warna = warna
        self.jarijari = jarijari
        self.material = material

    def get_volume(self):
        return (4 / 3) * 3.14 * (self.jarijari ** 3)
    
    def get_material(self):
        return self.material

# definisi konstanta biasanya menggunakan huruf kapital
class Material:
    KULIT = "Kulit"
    PLASTIK = "Plastik"
    BESI = "Besi"

# akses konstanta dengan menyebutkan 
# nama kelas (dot) nama atribut static
bola1 = Bola("Merah", 4, Material.PLASTIK)
bola2 = Bola("Hijau", 3, Material.KULIT)

print(bola1.get_material())     # 'Plastik'
print(bola2.get_material())     # 'Kulit'
```

Definisi konstanta secara `static` sebelumnya juga dapat diakomodir dengan menggunakan `enum`. Lebih lanjut mengenai `enum` dapat dilihat pada [dokumentasi Python](https://docs.python.org/3/library/enum.html).
