# Python Fundamentals (1): Variabel dan Tipe Data

## Halo, Gais!

Program paling sederhana, mencetak ke layar

```Python
print("Halo, Gais!")
```

## Halo, `nama`!

Program menerima masukan string lalu cetak ke layar sesuai dengan masukan

```Python
nama = input("Nama kamu: ")
print("Halo, " + nama + "!")
```

Perhatikan bahwa dalam pemrograman Python, kita tidak perlu mendefinisikan tipe data. Namun, perhatikan juga bahwa variabel `nama` juga harus bertipe `string` agar operasi penjumlahan (*string concatenation*) dapat dilakukan.

## Kalkulator sederhana

```Python
sisi = 2
volume = sisi * sisi * sisi
print("Volume kubus adalah: " + str(volume))
```

Menggunakan operator pangkat `**`

```Python
sisi = 2
volume = sisi ** 3
print("Volume kubus adalah: " + str(volume))
```
