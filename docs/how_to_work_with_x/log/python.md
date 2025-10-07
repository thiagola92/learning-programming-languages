# Python

??? abstract "Official"

    Esta biblioteca é mantida pelos criadores oficiais da linguagem.

A biblioteca segue parcialmente o padrão [syslog](https://en.wikipedia.org/wiki/Syslog).  

O comportamento padrão da biblioteca é ignorar todo log abaixo do level `logging.WARNING`, por isto adicionamos `logging.INFO`.  

## File

```python
import logging

logging.basicConfig(filename="example.log", level=logging.INFO)
logging.info("Example")
```

```
INFO:root:Example
```

## Stderr

```python
import logging

logging.basicConfig(filename=None, level=logging.INFO)
logging.info("Example")
```

```
INFO:root:Example
```