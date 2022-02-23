# Tes Otomatis

`unittest` adalah kerangka kerja standar untuk menjalankan pengujian kode dalam Python.

Untuk membuat `unittest` kita membuat kelas baru dan menuliskan skrip untuk menguji program pada kelas tersebut. Kita akan menulis rangkaian fungsi asesmen yang terdapat pada kelas `unittest.TestCase`.

Berikut merupakan contoh `unittest` yang ketika dijalankan akan memberikan pesan bahwa terdapat 1 tes sukses dan 1 tes gagal.

```Python
import unittest


class TestSum(unittest.TestCase):
    # skrip tes pada kenyataannya benar
    def test_sum(self):
        self.assertEqual(sum([1, 2, 3]), 6, "Seharusnya 6")

    # skrip tidak tepat, hanya untuk uji coba error saja
    def test_sum_tuple(self):
        self.assertEqual(sum((1, 2, 2)), 6, "Seharusnya 6")

if __name__ == '__main__':
    unittest.main()
```

Struktur sebuah `unittest` seharusnya mengikuti kerangka kerja berikut ini:

1. Definisi input
2. Eksekusi bagian kode (biasanya sebuah fungsi) dan merekam keluaran yang dihasilkan
3. Bandingkan keluaran program dengan keluaran yang diharapkan

Misalkan kita ingin menguji fungsi `sum()` yang kita buat pada modul dengan nama `skrip.py` seperti berikut:

```Python
def sum(arg):
    total = 0
    for val in arg:
        total += val
    return total
```

Untuk menguji fungi tersebut, kita membuat file `test_sum.py` berikut:

```Python
import unittest

from skrip import sum

class TestSum(unittest.TestCase):
    def test_list_int(self):
        """
        Test that it can sum a list of integers
        """
        data = [1, 2, 3]
        result = sum(data)
        self.assertEqual(result, 6)

if __name__ == '__main__':
    unittest.main()
```

Untuk menjalankan skrip ujicoba dapat digunakan

```Python
python -m unittest test_sum
```
