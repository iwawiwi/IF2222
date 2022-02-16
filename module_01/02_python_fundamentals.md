# Python Fundamentals (2): Kondisi

## Contoh program dengan pengecekan kondisi

```Python
passw = input("Masukkan password: ")
real_passw = "p45sw0rdR4ha51a!"

if passw == real_passw:
  print("OK :)")
else:
  print("Password tidak sesuai :(")
```

Perhatikan indentasi dalam Python menyatakan blok program.

## Percabangan `IF`

```Python
x = input("Masukan nilai x: ")
if (x > 0):
    print("x bilangan positif")
```

## Percabangan `IF-ELSE`

```Python
x = input("Masukan nilai x: ")
if (x > 0):
    print("x bilangan positif")
else:
    print("x bilangan negatif")
```

## Percabangan `IF-ELIF-ELSE`

```Python
x = input("Masukan nilai x: ")
if (x > 0):
    print("x bilangan positif")
elif (x < 0):
    print("x bilangan negatif")
else:
    print("x adalah nol")
```
