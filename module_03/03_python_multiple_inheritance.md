# Pewarisan berganda (*multiple inheritance*)

Python memungkinkan pewarisan berganda. Conthonya adalah sebagai berikut:

```Python
class A(object):
    pass

class B(object):
    def __str__(self):
        return "dari kelas B"

    pass

class C(A, B):
    pass

c = C()
print(c)    # 'dari kelas B'
```

Namun, pewarisan berganda ini dapat menyebabkan problematika pada kondisi ***diamond problem***. Contoh diatas sebenarnya merupakan salah satu kasus dari *diamond problem* dalam pewarisan berganda.

Jika anda ingin menerapkan konsep pewarisan berganda dalam program, anda harus hati-hati dalam melakukan implementasinya. Anda bisa saja menghadapi kejadian *diamond problem*. Lebih jelasnya perhatikan contoh berikut:

```Python
class GrandParent:
    def fn(self):
        print("fungsi di kelas GrandParent")

class ParentA(GrandParent):
    pass

class ParentB(GrandParent):
    def fn(self):
        print("fungsi di kelas ParentB")

class Child(ParentA, ParentB):
    pass

anak = Child()
anak.fn()
```

Perhatikan bahwa kelas `Child` memiliki *parent class* `ParentA` dan `ParentB`, dimana juga *parent class* ini merupakan *child class* dari `GrandParent`. Fungsi `fn` dari kelas `GrandParent` diwariskan ke `ParentA` dan `ParentB`. Pada kelas `ParentB`, fungsi di-*override*. Jika program diatas dieksekusi, ternyata fungsi `fn` pada objek `anak` yang merupakan kelas `Child` merupakan implementasi dari `fn` pada kelas `ParentB`. Mengapa tidak menjalankan fungsi `fn` pada `GrandParent` yang diwariskan pada kelas `ParentA`? Dalam hal ini, Python memiliki mekanisme untuk mengatasi *diamond problem* dalam pewarisan berganda dengan menerapkan algoritma C3 untuk melakukan **MRO (*method resolution order*)**. Anda dapat mengetahui bagaimana Python menelusuri urutan fungsi yang dipanggil dengan menggunakan fungsi `mro()`:

```console
>>Child.mro()
output : [<class 'Child'>, <class 'ParentA'>, <class 'ParentB'>, <class 'GrandParent'>, <class 'object'>]
```

Detail dari MRO tidak akan dijelaskan disini. Anda dapat melihat algoritma MRO yang digunakan mulai dari Python 2.3 hingga saat ini (Python 3.10) [disini](https://www.python.org/download/releases/2.3/mro/).
