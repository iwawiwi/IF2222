# Python Fundamentals (9): Dictionary

Setiap elemen dalam tipe data kamus atau Dictionary terdiri dari pasangan kunci dan nilai (key-value). Kunci merupakan nama unik untuk identifikasi nilai sebuah elemen dalam Dictionary

```Python
empty_dictionary = {}

ibukota = {"Lampung":"Bandar Lampung", "Bali":"Denpasar", "Papua":"Jayapura"}
bilangan_kubik = {1:1, 2:8, 3:27, 4:64}
gaje = {1:"Ahmad", "18":False, "Warna":"Biru"}
```

Membuat dictionary dari tupel dan list

```Python
tuple_of_tuples = (
  ("Lampung", "TKG"),
  ("Bali", "DPS"),
  ("Jakarta", "JKT")
)
ibukota = dict(tuple_of_tuples)

list_of_tuples = [
  ("Lampung", "TKG"),
  ("Bali", "DPS"),
  ("Jakarta", "JKT")
]
capitals = dict(list_of_tuples)
```
