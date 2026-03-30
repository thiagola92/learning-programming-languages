# Python
??? abstract "Adaptation"

    Esta linguagem possui uma adaptação do conceito.

## List
É uma alternativa para arrays.  

```python
a = [1, 10, 100]

print(f"a = {a}")
```

```
a = [1, 10, 100]
```

## Array
A linguagem providência a classe ([`array`](https://docs.python.org/3/library/array.html)) para simular alguns comportamentos de um array.  

```python
from array import array

a = array('i', [1, 10, 100])

print(f"a = {a}")
```

```
a = array('i', [1, 10, 100])
```