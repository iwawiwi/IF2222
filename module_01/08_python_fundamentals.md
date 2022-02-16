# Python Fundamentals (8): Set

Set tidak mengijinkan elemen yang sama dimuat dalam satu variabel (unik). Elemen dalam Set tidak tercatat urutannya saat didefinisikan.

```Python
set_karakter = {'a', 'b', 'c'}
set_satu_elemen = {250}

# elemen duplikat terhapus
s1 = {1, 1, 1, 1, 2}
print(s1) # {1, 2}

# sets tidak mencatat urutan elemen
s2 = {3, 1, 2}
print(s2) # {1, 2, 3}
```

Perlu memperhatikan perbedaan antara Set kosong dengan Dictionary

```Python
# cara deklarasi set kosong
set_kosong = set()
print(type(empty_set))  # <class 'set'>

# berikut ini bukan merupakan set kosong, tetapi sebuah dictionary kosong
empty_dict = {}
print(type(empty_dict)) # <class 'dict'>
```

Operasi pada set

```Python
s = {2, 7, 3, 4, 7}
print(s)            # {2, 3, 4, 7}
print(len(s))       # 4
print(7 in s)       # True
print(8 not in s)   # True

s.add(5)
print(s) # {2, 3, 4, 5, 7}
s.remove(7)
print(s) # {2, 3, 4, 5}
s.update({5, 6})
print(s) # {2, 3, 4, 5, 6}
```

Operasi khusus pada set

```Python
s1 = {1, 2, 4}
s2 = {2, 3}

# intersection
print(s1 & s2) # {2}
# union
print(s1 | s2) # {1, 2, 3, 4}
# difference
print(s1 - s2) # {1, 4}

# symetric difference
print((s1 - s2) | (s2 - s1)) # {1, 3, 4}
print(s1 ^ s2)               # {1, 3, 4}
```

Operasi khusus dengan menggunakan fungsi built-in pada set

```Python
s1 = {1, 2, 4}
s2 = {2, 3}

print(s1.intersection(s2))          # {2}
print(s1.union(s2))                 # {1, 2, 3, 4}
print(s1.difference(s2))            # {1, 4}
print(s1.symmetric_difference(s2))  # {1, 3, 4}
```

Operasi khusus untuk subset dan superset

```Python
s1 = {1, 2}
s2 = {1, 2, 3}
s3 = {3, 4}

print(s1 <= s2) # True
print(s2 >= s1) # True
print(s1 <= s3) # False
print(s1 <= s1) # True
```
