# Python Fundamentals (6): Lists

Untuk menyimpan data yang ukurannya lebih dari satu elemen ke dalam satu variabel, kita dapat memanfaatkan tipe data List.

```Python
daftar_game = ["Starcraft 2", "FIFA", "Forza", "Red Dead Redemption"]
daftar_tahun = [2020, 2021, 2022, 2023, 2024]
```

Elemen dalam list juga dapat berupa list. Kita menggunakan list dalam list ketikan merepresentasikan array multidimensi

```Python
list_of_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]] # matriks 3x3 
```

Tidak seperti dalam bahasa pemrograman `C++`, list dalam Python dapat memiliki nilai elemen yang berbeda tipe.

```Python
data_siswa = ["Ahmad", 10, False] # nama, umur, punya_laptop
```

Indexing dan slicing pada list pada dasarnya sama dengan [indexing & slicing pada string](python_fundamentals_04.md)

```Python
data_siswa = ["Ahmad", 10, False]
print(data_siswa[1])    # cetak 10
print(data_siswa[-1])   # cetak False
print(data_siswa[:2])   # cetak ["Ahmad", 10]
```

Contoh operasi list.

```Python
daftar_kegiatan = ["bangun pagi", "sarapan", "mandi"]
print("belajar" in daftar_kegiatan) # cetak False
print(len(daftar_kegiatan))         # cetak 3

# append list
daftar_kegiatan = daftar_kegiatan + ["belajar"]
# hapus elemen
del daftar_kegiatan[1] 
```

Iterasi pada list

```Python
daftar_kegiatan = ["sarapan", "mandi", "belajar"]

for kegiatan in daftar_kegiatan:
    print(kegiatan)

for i in range(len(daftar_kegiatan)):
    print(daftar_kegiatan[i])
```

Fungsi-fungsi dalam list

```Python
daftar_kegiatan = ["sarapan", "mandi", "belajar"]

print(daftar_kegiatan.index("belajar")) # 2
print(daftar_kegiatan.pop())  # belajar
print(daftar_kegiatan)        # ["sarapan", "mandi"]
daftar_kegiatan.append("kuliah")                  
print(daftar_kegiatan)        # ["sarapan", "mandi", "kuliah"]

daftar_kegiatan.reverse()
print(daftar_kegiatan) # ["kuliah", "mandi", "sarapan"]
daftar_kegiatan.remove("kuliah")
print(daftar_kegiatan) # ["mandi", "sarapan"]
daftar_kegiatan.extend(["olahraga", "istirahat"])
print(daftar_kegiatan) # ["mandi", "sarapan", "olahraga", "istirahat"]
daftar_kegiatan.sort()
print(daftar_kegiatan) # ["istirahat", "mandi", "olahraga", "sarapan"]
```
