# Python Fundamentals (5): Fungsi

Cara deklarasi fungsi menggunakan keyword `def`

```Python
def faktorial(n): # signature
    # body
    result = 1
    for i in range(1, n+1):
        result *= i
    return result # return value
```

Deklarasi fungsi dengan *type hints*

```Python
def faktorial(n: int) -> int: # signature dengan type-hint
    # body
    result = 1
    for i in range(1, n+1):
        result *= i
    return result # return value
```
