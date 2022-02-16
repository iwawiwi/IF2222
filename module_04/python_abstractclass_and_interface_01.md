# Python Abstract Class and Interface

Lihat kembali problem yang terjadi pada modul sebelumnya terkait dengan [Inheritance](python_inheritance.md)

Permasalahan dapat terjadi jika kita membuat objek `Employee` dan menghitung gaji yang didapat dengan menggunakan fungsi `calculate_payroll`.

```Python
emp = Employee(1, "IE")
payroll_system = PayrollSystem()

# INVALID call
payroll_system.calculate_payroll([emp])
```

Saat ini `Employee` masih berupa kelas biasa! Abstract Base Class (`ABC`) dalam Python dapat dimanfaatkan untuk hal ini. Kelas yang mewarisi kelas `ABC` tidak dapat dibuat objeknya, namun kelas tersebut dapat menjadi kelas basis objek lainnya.

```Python
from abc import ABC, abstractmethod

class _Employee(ABC):
    def __init__(self, id, name):
        self.id = id
        self.name = name

    @abstractmethod
    def calculate_payroll(self):
        pass 
```

Setiap kelas yang mewarisi kelas `_Employee` wajib melakukan implementasi detail dari fungsi yang diberikan tanda (disebut juga sebagai dekorator) `@abstractmethod` dalam hal ini `calculate_payroll()`. Jika anda mencoba untuk membuat objek dari kelas `_Employee`, interpreter Python akan memberikan pesan kesalahan yang memberikan informasi bahwa kelas abstrak `_Employee` tidak dapat di-instansiasi.

Mungkin ada pertanyaan, mengapa kita tidak membuat saja kelas `Employee` yang juga mengimplementasikan fungsi `calculate_payroll()`?

* Pewarisan memodelkan hubungan `adalah`. Contohnya, kelas `Customer` dapat juga memiliki atribut `id` dan `name`. Namun, `Customer` **bukan** `Employee`, sehingga tidak tepat jika `Customer` mewarisi `Employee`.
* Ketika kita ingin menggunakan kembali implementasi kelas yang sudah pernah dibuat kedalam bagian program dalam aplikasi, kita hanya perlu mewarisi kelas basis dan melakukan implementasi fungsi dan atribut yang dibutuhkan saja. Kelas basis tidak perlu didefinisikan kembali.

Jika
