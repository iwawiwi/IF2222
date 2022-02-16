# Python Fundamentals (7): Tupel

Tupel mirip seperti list namun sekali terdefinisi, elemen tupel tidak dapat diubah. Berikut merupakan cara membuat tupel

```Python
tupel_1 = (28, 28, 3)
tupel_2 = 28, 28, 3
tupel_satu_dimensi = (3,)
tupel_kosong = ()

tupel_3 = tuple("abc")
print(tupel_3)      # ("a", "b", "c")
tupel_4 = tuple([28, 28, 3])
print(tupel_4)      # (28, 28, 3)
tupel_5 = tuple(range(3))
print(tupel_5)      # (0, 1, 2)
tupel_6 = tuple()
print(tupel_6)      # ()

tuple_1[2] = 1 # ERROR!
```

Bedakan tupel satu dimensi dengan elemen dengan satu nilai

```Python
ini_tupel = ("objek",)
print(type(ini_tupel))         # merupakan tupel
ini_bukan_tupel_1 = ("objek")
print(type(ini_bukan_tupel_1)) # merupakan string
ini_bukan_tupel_2 = (100)
print(type(ini_bukan_tupel_2)) # merupakan int
```

> **Mutable**: elemen dapat diubah setelah didefinisikan<br />
> **Immutable**: elemen tidak dapat diubah setelah didefinisikan<br />

Jika ingin mengubah elemen, objek data yang baru harus dibuat. `list` termasuk tipe data mutable, termasuk juga `dict` dan `set`. `tuple` termasuk tipe data immutable, termasuk juga `int`, `float`, `complex`, `boolean`, dan `str`
