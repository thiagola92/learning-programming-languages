# Python

Igual a outras linguagens, é possível inciar o debugger pela linha de comando.  

```python
python3 -m pdb main.py
```

Porém o debugger é embutido na linguagem, ou seja, você pode explicamente adicionar um breakpoint na linguagem.  

```python
print("Hello")
breakpoint()
print("World")

a = 10
b = 20; breakpoint()
print(a+b)
```
