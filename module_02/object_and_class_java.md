# Mutable and Immutable Object dalam Java

Objek yang *immutable* merupakan objek yang konten atau propertinya tidak dapat diubah setelah objek dibuat. Objek yang *immutable* dibangun dari kelas yang juga bersifat *immutable*. Contoh, kelas `String` adalah kelas yang *immutable*. Objek `String` juga merupakan objek *immutable*.

Sarat kelas yang *immutable*:

- Seluruh atribut atau properti harus bersifat `private`;
- Tidak ada fungsi `setter`; dan
- Fungsi `getter` tidak boleh mengembalikan objek yang bersifat *mutable*. Jika ada, fungsi `getter` hanya mengembalikan objek yang *immutable*.

Contoh kelas yang *immutable* (Java):

```Java
class A {
    // atribut bersifat private
    private int x;

    public A(int x) {
        this.x = x;
    }

    public int getX() {
        // tipe data int (primitif) merupakan objek immutable 
        return this.x;
    }
}
```

Contoh kelas yang *mutable* (Java):

```Java
class B {
    private int x;

    public B(int x) {
        this.x = x;
    }

    // fungsi setter menyebabkan kelas bersifat mutable 
    public setX(x) {
        this.x = x;
    }
}

```

Berdasarkan contoh kelas (dalam Java) berikut ini, tentukan apakah merupakan kelas *mutable* atau kelas *immutable*!

```Java
class C {
    private int x;
    private B b;

    public C(int x, B b) {
        this.x = x;
        this.b = b;
    }

    public getX() {
        return this.x;
    }
}
```

Kelas ini bersifat *immutable* karena seluruh sarat kelas yang *immutable* telah terpenuhi!
