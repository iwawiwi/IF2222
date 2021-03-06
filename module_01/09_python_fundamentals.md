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
airport_code = dict(tuple_of_tuples)

list_of_tuples = [
  ("Lampung", "TKG"),
  ("Bali", "DPS"),
  ("Jakarta", "JKT")
]
code_airport = dict(list_of_tuples)
```

Kita dapat menggunakan kunci sebagai indeks untuk mendapatkan nilai yang dipetakan oleh sebuah kunci dalam dictionary. Perhatikan bahwa ketika kunci tidak didefinisikan, akan muncul error ketika kita mencoba mengakses kamus menggunakan kunci tersebut.

```Python
kode_bandara = {"Lampung":"TKG", "Bali":"DPS", "Jakarta":"CGK"} 
print(kode_bandara["Bali"])     # DPS
print(kode_bandara["Lampung"])  # TKG

bilangan_kubik = {1:1, 2:8, 3:27, 4:64} 
print(bilangan_kubik[3])        # 27
print(bilangan_kubik[1])        # 1

print(bilangan_kubik[5])        # key-ERROR
```

Untuk menambahkan, mengubah, dan menghapus pasangan key-value pada dictonary, kita dapat menambahkannya satu demi satu dengan cara sebagai berikut

```Python
kode_bandara = {"Lampung":"TKG", "Bali":"DPS", "Jakarta":"CGK"} 

# tambah kode bandara sumatera utara
kode_bandara["Sumatera Utara"] = "KNO"
print(kode_bandara)
# update kode bandara jakarta
kode_bandara["Jakarta"] = "HLP"
# hapus kode bandara bali
del kode_bandara["Bali"]

print("Jakarta" in kode_bandara)  # True
print("Bali" in kode_bandara)     # False
```

Operasi lainnya pada kamus

```Python
kode_bandara = {"Lampung":"TKG", "Bali":"DPS", "Jakarta":"CGK"} 
daftar_suara = ["enrinal", "huda", "ivena", "enrinal", "enrinal", "huda”", …]

print(len(kode_bandara)) # 3

# update lebih dari satu kode bandara
y = {"Sumatera Utara":"KNO", "Papua":"DJJ"}
kode_bandara.update(y)

# daftar seluruh kunci yang ada dalam tipe data list
daftar_kunci = list(kode_bandara.keys())

# hapus semua pasangan key-value dalam kamus
capitals.clear()
```

Iterasi pada `dictionary` dapat dilakukan seperti iterasi pada list biasa

```Python
kode_bandara = {"Lampung":"TKG", "Bali":"DPS", "Jakarta":"CGK"}

# variabel kota berisi key
for kota in kode_bandara:
  print(kota, "kode bandaranya adalah" , kode_bandara[kota])

# items() mengembalikan pasangan key dan value
for kota, kode in kode_bandara.items():
  print(kota, "kode bandaranya adalah" , kode)
```

<!--
## Latihan (PR)

```Python
# 1. Jack's dictionary
jack = { "name":"Jack Frost",
         "assignment" : [80, 50, 40, 20],
         "test" : [75, 75],
         "lab" : [78.20, 77.20]
       }
# 2. James's dictionary
james = { "name":"James Potter",
          "assignment" : [82, 56, 44, 30],
          "test" : [80, 80],
          "lab" : [67.90, 78.72]
        }
# 3. Dylan's dictionary
dylan = { "name" : "Dylan Rhodes",
          "assignment" : [77, 82, 23, 39],
          "test" : [78, 77],
          "lab" : [80, 80]
        }  
# 4. Jessica's dictionary
jess = { "name" : "Jessica Stone",
         "assignment" : [67, 55, 77, 21],
         "test" : [40, 50],
         "lab" : [69, 44.56]
       }
# 5. Tom's dictionary
tom = { "name" : "Tom Hanks",
        "assignment" : [29, 89, 60, 56],
        "test" : [65, 56],
        "lab" : [50, 40.6]
      }
```
->
