# Operator overloading

Pada mater sebelumnya mengenai [polimorfisme](04_python_polymorphism.md) kita telah mengetahui bahwa ada dua teknik yang dapat dilakukan untuk menghasilkan polimorfisme dalam tingkat kelas (*overriding*) dan fungsi (*overloading*). Kali ini kita akan membahas terkait dengan teknik overloading untuk menghasilkan polimorfisme pada tingkatan operator.

## Polimorfisme level operator

Sebagai gambaran terkait polimorfisme pada tingkatan operator, perhatikan kasus berikut terkait dengan operator `+` (tambah) pada Python:

```Python
print(1 + 4)                # 5
print("Belajar" + "PBO")    # 'Belajar PBO'
```

Dari contoh, operator `+` dapat memiliki dua perilaku yang berbeda jika kita mengoperasikannya dengan tipe data tertentu. Pada umumnya, di banyak bahasa pemrograman lainnya, operator `+` terdefinisi untuk penjumlahan dua data numerik. Hal ini juga berlaku dalam bahasa pemrograman Python. Namun sebagai tambahannya, jika kita menggunakan operator `+` untuk operasi tipe data `str` (string), yang dihasilkan adalah penggabungan string. Hal ini salah satu contoh dari penerapan polimorfisme di tingkat operator, dimana sebuah operator dapat memiliki peran yang berbeda bergantung pada tipe data yang dioperasikan.

Kita dapat juga mendefinisikan kembali operator *built-in* dalam Python untuk tipe data yang kita definisikan sendiri. Sebagai contoh, kita dapat saja membuat objek dengan tipe `Waktu` (merupakan instance dari kelas `Waktu`. Kita dapat melakukan *overloading* pada operator `+` untuk dapat beroperasi dengan tipe data `Waktu` ini. Perhatikan contoh berikut:

```Python
class Waktu:
    def __init__(self, jam, menit, detik):
      self.jam = jam
      self.menit = menit
      self.detik = detik

    def __str__(self):
        return "{:02d} : {:02d} : {:d}".format(self.jam, self.menit, self.detik)
    
    def __add__(self, other):
        if not isinstance(other, Waktu):
            return NotImplemented
        ovf_detik = (self.detik + other.detik) // 60
        detik = (self.detik + other.detik) % 60
        ovf_menit = (self.menit + other.menit + ovf_detik) // 60
        menit = (self.menit + other.menit + ovf_detik) % 60
        ovf_jam = (self.jam + other.jam + ovf_menit) // 24 # bisa diabaikan
        jam = (self.jam + other.jam + ovf_menit) % 24
        
        return Waktu(jam, menit, detik) 

jam_a = Waktu(1, 59, 50)
print(jam_a)
jam_b = Waktu(3, 56, 58)
print(jam_b)

print(jam_a + jam_b)
```

Jika anda perhatikan program sebelumnya, untuk menghasilkan polimorfisme di tingkat operator, kita dapat mendefinisikan fungsi `__add__()` pada kelas `Waktu` agar memungkinkan operasi penjumlahan antara dua objek `Waktu` dengan menggunakan operator `+`. Jangan lupa juga, kita mendefinisikan fungsi `__str__()` agar objek `Waktu` dapat dicetak dengan memberikan informasi yang relevan (dalam hal ini mencetak sesuai format waktu `hh:mm:ss`). Sebenarnya hanya dengan mendefinisikan fungsi `__add__()` saja tanpa perlu mendefinisikan fungsi `__str__()`, kita sudah memungkinkan objek `Waktu` untuk dapat dioperasikan dengan operator `+`. Kita juga dapat mendefinisikan berbagai macam operator bawaan Python untuk melakukan overloading di tingkat operator. Silahkan kunjungi [referensi berikut](https://www.programiz.com/python-programming/operator-overloading) untuk menyesuaikan operator dan fungsi yang dapat diimplementasikan untuk memungkinkan overloading pada tingkat operator.

Referensi: [Programiz - Operator Overloading](https://www.programiz.com/python-programming/operator-overloading)
