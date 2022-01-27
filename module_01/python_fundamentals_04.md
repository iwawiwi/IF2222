# Python Fundamentals (4): Indexing & Slicing

Indexing

```Python
s = "INFORMATIK"
# dua perintah berikut mencetak karakter yang sama dari s
print(s[4])     # cetak R
print(s[-6])    # cetak R
```

Slicing

```Python
s = "INFORMATIK"
# dua perintah berikut mencetak karakter yang sama dari s
print(s[2:6])   # cetak FORM
print(s[2:])    # cetak FORMATIK
```

Operasi String

```Python
s = "Among Us"

# panjang karakter s
print(len(s))

# menyambung string (konkatenasi)
t = "1 Impostor " + s
print(t)

# duplikasi string
u = "ha" * 3
print(u)

# cek apakah substring terkadung dalam string s
print("Us" in s)

# print seluruh karakter dalam s
for c in s:
  print(c)
```

Fungsi pada String

```Python
s = "Among Us"
# megubah string menjadi lower case
print(s.lower())

# cek apakah string berupa digit angka
print(s.isdigit()) # False

# cari sub-string, kembalikan indeks pertama kemunculan 
# -1 jika tidak ketemu
print(s.find("Us")) # 6

# pisahkan string menjadi token, dipisahkan dengan spasi
print(s.split()) # ['Among', 'Us']

# Format string sesuai parameter yang diberikan
print("Let's play {0} with {1}!".format(s, "friends"))

# Mengganti sub string (jika ditemukan)
print(s.replace("Us", "Them")) # Among Them
```
