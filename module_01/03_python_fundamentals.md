# Python Fundamentals (3): Perulangan

## Perulangan dengan `while`

```Python
passw = input("Masukkan password: ") 
real_passw = "p45sw0rdR4ha51a!" 

while passw != real_passw:
    print("Password tidak sesuai :(")
    passw = input("Masukkan password: ")

print("OK :)")

```

## Perulangan dengan `for`

Kode berikut akan mencetak secara terurut angka 0 sampai 9

```Python
for i in range(10):
    print(i)
```

Kode berikut akan mencetak secara terurut angka 5 sampai 9

```Python
for i in range(5, 10):
    print(i)
```

Kode berikut akan mencetak bilangan ganjil dari 1 sampai 10 (inklusif)

```Python
for i in range(1, 10, 2):
    print(i)
```

Selain list dengan nilai angka, `for` loop dapat dilakukan untuk list bertipe string.

```Python
for s in ["satu", "dua", "tiga"]:
    print(s)
```
