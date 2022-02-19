# Kelas dan Objek dalam Python

Perhatikan program yang tanpa menerapkan konsep berikut ini untuk mendefinisikan dua buah kubus:

```Python
kubus1_sisi = 2
kubus2_sisi = 4

kubus1_warna = "Merah"
kubus2_warna = "Hijau"

print(f"Kubus pertama memiliki panjang sisi {kubus1_sisi} dan warna {kubus1_warna}")
print(f"Kubus kedua memiliki panjang sisi {kubus2_sisi} dan warna {kubus2_warna}")
```

Bagaimana kalau anda diminta untuk menambahkan 10 kubus yang berbeda lagi? Pasti sangat ribet!! Dengan menggunakan konsep OOP, program ini dapat dibuat menjadi lebih ringkas dan lebih intuitif.

```Python
class Kubus:
    def __init__(self, sisi, warna):
        self.sisi = sisi
        self.warna = warna
    
    def to_string(self):
        print(f"Kubus memiliki panjang sisi {self.sisi} dan warna {self.warna}")

kubus1 = Kubus(2, "Merah")
kubus2 = Kubus(4, "Hijau")
kubus3 = Kubus(3, "Kuning")
kubus4 = Kubus(2, "Biru")
...

kubus1.to_string()
kubus2.to_string()
kubus3.to_string()
...
```

Perhatikan kode diatas, kita membuat sebuah kelas dengan nama `Kubus`. Sebuah kelas dalam Python dikenali dengan diawali kata kunci `class`. Kelas mendefinisikan atribut dan perilaku (semacam *blueprint*) objek yang nantinya akan dibuat.

Berikut ini adalah contoh definisi kelas `Bola` yang memiliki dua atribut yaitu `warna` dan `jarijari`; juga memiliki satu buah fungsi `get_volume` yang mengembalikan besaran volume dari sebuah bola dengan `jarijari` tertentu.

```Python
class Bola:
    # merupakan konstruktor dengan dua parameter
    def __init__(self, warna, jarijari):
        self.warna = warna          # atribut warna
        self.jarijari = jarijari    # atribut jarijari

    # fungsi menghitung volume bola
    def get_volume(self):
        # rumus volume bola
        return (4 / 3) * 3.14 * (self.jarijari ** 3) 
```

<!-- TODO: Definisi UML -->

Setiap objek dibuat dari sebuah kelas melalui proses `instansiasi`. Objek memiliki atribut dan perilaku yang terdefinisi dari kelas yang bersesuaian. Untuk membuat objek `bola1` dengan atribut warna `"Merah"` dan jari-jari `4`, kita memanggil konstruktor kelas `Bola` yang memiliki dua parameter dengan cara sebagai berikut:

```Python
bola1 = Bola("Merah", 4)
```

atau bisa juga dengan menggunakan named parameter:

```Python
bola1 = Bola(jarijari=4, warna="Merah")
```

Begitu pula jika kita ingin membuat objek baru `bola2` dengan atribut warna "Hijau" dan jari-jari `3`:

```Python
bola2 = Bola("Hijau", 3)
```

Ketika kita akan membuat objek baru (atau disebut juga **instansiasi**), secara otomatis fungsi `__init__()` akan dieksekusi oleh interpreter Python.

Setelah objek dibuat, kita dapat mengakses atribut dan fungsi pada objek tersebut dengan cara sebagai berikut:

```Python
print(bola1.warna)          # merah
print(bola1.jarijari)       # 4

print(bola1.get_volume())   # 267.946666666....
```

Setiap variabel menyimpan referensi objek. Contoh berikut memberikan ilustrasi bahwa objek `bola2` merujuk pada objek `bola1`:

```Python
bola1 = Bola("Merah", 4)
bola2 = bola1

bola1 == bola2  # True
id(bola1)       # id 140515279628704
id(bola2)       # id 140515279628704
```

Perhatikan bahwa objek `bola2` memiliki `id` yang sama dengan `bola1` yang menyatakan bahwa `bola2` merupakan referensi yang sama dengan `bola1`. Jika kita merubah properti pada objek `bola2`, itu sama saja dengan mengubah properti `bola1`.

```Python
# masih menggunakan referensi yang sama dengan bola1
bola2.warna = "Biru" 

bola2.warna     # 'Biru'
bola1.warna     # 'Biru'
```

Setiap proses instansiasi mengakibatkan sebuah objek baru dibuat dan tersimpan dalam memori. Perhatikan kode berikut ini, meskipun kita mendefinisikan atribut yang sama untuk kedua objek `Bola`, namun kedua objek ini merujuk pada objek yang berbeda dalam memori.

```Python
bola1 = Bola("Merah", 4)
bola3 = Bola("Merah", 4)

bola1 == bola2  # False
id(bola1)       # id 140515279628704
id(bola2)       # id 140515279628752
```

Dalam bahasa pemrograman Java kita dapat mendefinisikan `null` pointer sebagai referensi dari sebuah objek yang berarti objek tersebut tidak merujuk alamat memori tertentu. Dalam Python, konsep `null` ini setara dengan `None`. Namun dalam Python, `None` merujuk pada alamat memori yang sudah didefinisikan dan tidak berasosiasi dengan objek tertentu dalam program.
