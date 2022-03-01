# Polimorfisme dalam Python

Dalam OOP, **polimorfisme** memungkinkan sebuah objek yang sama dapat memiliki perilaku yang bermacam-macam sesuai konteksnya. Dalam OOP terdapat berbagai cara untuk memungkinkan polimorfisme objek.

## Polimorfisme tingkat kelas

Perhatikan contoh program berikut.

```Python
class Shape:
    def draw(self):
        print("Draw a shape")

class Circle(Shape):
    def draw(self):
        print("Draw a circle")

class Rectangle(Shape):
    def draw(self):
        print("Draw a rectangle")

def draw_shape(shp):
    if isinstance(shp, Shape):
        shp.draw()

circle = Circle()
rectangle = Rectangle()

shapes = [circle, rectangle]
for s in shapes:
    draw_shape(s)
```

output program adalah:

```bash
Draw a circle
Draw a rectangle
```

Pada materi [overriding](02_python_overriding.md) kita membahas bahwa kita dapat mendefinisikan kembali fungsi yang diwarsikan dari *parent-class*. Dalam kasus diatas, kita melihat bahwa kita mendefinisikan kembali fungsi `draw()` pada *child-class* `Circle` dan `Rectangle`. Perhatikan juga fungsu `draw_shape()` yang didefinisikan pada program utama. Fungsi `draw_shape()` ini menerima parameter berupa objek `Shape`. Perhatikan pada bagian pengecekan berikut yang ada pada fungsi `draw_shape()`:

```Python
if isinstance(shp, Shape):
    shp.draw()
```

Fungsi `isinstance()` merupakan fungsi bawaan Python untuk mengecek apakah sebuah objek (`shp`) merupakan *instance* dari kelas tertentu (`Shape`), sehingga kita memastikan bahwa fungsi `draw()` yang terdapat pada kelas `Shape` dapat dipanggil. Satu pertanyaan yang mungkin muncul adalah, mengapa objek dari kelas `Circle` dan `Rectangle` dapat dikategorikan sebagai *instance* dari kelas `Shape`? Dalam konsep pewarisan, kita mendefinisikan relasi antara *child-class* dan *parent-class* sebagai relasi `adalah` (atau ***is a***). Jadi, dalam kasus diatas, kita mendefinisikan relasi antara kelas `Circle`, `Rectangle`, dan `Shape` bahwa:

- `Circle` merupakan/adalah `Shape`; dan
- `Rectangle` merupakan/adalah `Shape`

tapi perlu diingat, relasi pewarisan juga berakibat bahwa:

- `Shape` bukan merupakan `Circle`; dan
- `Shape` bukan merupakan `Rectangle`

Relasi yang berlaku adalah: *child-class* ***is a*** *parent-class*. Relasi beriku **tidak** berlaku: *parent-class* ***is a*** *child-class*.

Kembali lagi pada program diatas, objek `circle` dan `rectangle` masing-masing merupakan instance dari kelas `Circle` dan `Rectangle`. Berdasarkan relasi pewarisan, kita juga dapat menyatakan bahwa objek `circle` dan `rectangle` juga merupakan `Shape`. Kemudian, karena kita mendefinisikan kembali fungsi `draw()` pada kelas `Circle` dan `Rectangle` dengan menerapkan teknik *overriding*, pemanggilan fungsi `draw()` pada fungsi `draw_shape()` akan menyesuaikan implementasi dari kelas `Circle` dan `Rectangle` dan bukan memanggil fungsi `draw()` dari kelas `Shape`. Satu hal yang dapat disimpulkan disini bahwa kita telah menerapkan konsep **polimorfisme** pada level kelas. Kita dapat melihat bahwa objek `circle` dan `rectangle` dapat berperan sebagai objek dari kelas `shape`. Selain itu juga fungsi `draw()` dapat memiliki perlikau yang berbeda sesuai dengan implementasi objeknya.

## Polimorfisme tingkat fungsi

Jika kita memiliki dua atau lebih fungsi melakukan hal yang sama, sangat alami rasanya jika kita memberikan nama fungsi yang sama pada fungsi tersebut. Dalam Python, fungsi dengan detail implementasi yang berbeda (namun tujuannya sama) dapat diberikan dengan nama yang sama. Perhatikan contoh berikut ini:

```Python
def fungsi_linear(a, x, b=0):
    return a*x + b

print(fungsi_linear(2, 3))      # 6
print(fungsi_linear(2, 3, 1))   # 7
```

Fungsi `fungsi_linear()` dapat dipanggil dengan menspesifikasikan minimal 2 argumen yaitu `a` dan `x`. Namun, fungsi ini juga dapat dipanggil dengan menspesifikasikan 3 argumen, yaitu dengan menambahkan argumen `b` pada pemangilan fungsi.

Teknik yang serupa pada fungsi diatas dapat diimplementasikan dengan menggunakan `*args` maupun `**kwargs`:

```Python
def fungsi_linear(*args):
    pass

def fungsi_linear(**kwargs):
    pass

fungsi_linear(2, 3, 8)
fungsi_linear(a=2, x=3, b=8)
```
