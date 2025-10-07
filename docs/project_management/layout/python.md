# Python

??? abstract "Not Imposed"

    A linguagem deixa importar código de arquivos sem ligar para a localização deles. Por exemplo:
    
    ```python
    import code
    import dir/code
    import dir/dir/code
    import ../code
    ```

## src layout

Os códigos do seu projeto deve ficar dentro de um diretório reservado para o pacote/projeto, que por sua vez deve ficar dentro do diretório `src`.  
    
```
.
├── .gitignore
├── pyproject.toml
├── README.md
├── src/
│   └── my_package/
│       ├── file0.py
│       ├── file1.py
│       ├── file2.py
│       └── ...
└── tests/
    ├── test0.py
    ├── test1.py
    └── ...
```

Em outras palavras, se você fosse escrever o primeiro arquivo do seu projeto e o nome do arquivo fosse `main.py`, ele deveria ser escrito em:  

```
src/<package_name>/main.py
```

E no momento de distribuir, todos os pacotes dentro de `src` seriam importaveis pelo programador.  

```python
import my_package
```

Este layout reserva um diretório inteiro apenas para todos os pacotes a serem distribuidos. Embora a norma seja ter um pacote por distribuição, é possível se ter multiplos pacotes:  

```
.
├── .gitignore
├── pyproject.toml
├── README.md
├── src/
│   ├── my_package/
│   │   ├── file0.py
│   │   ├── file1.py
│   │   ├── file2.py
│   │   └── ...
│   └── my_package2/
│       ├── file3.py
│       ├── file4.py
│       ├── file5.py
│       └── ...
└── tests/
    ├── test0.py
    ├── test1.py
    └── ...
```

Isso faria ambos os pacotes my_package e my_package2 serem importáveis.  

```python
import my_package
import my_package2
```

## flat layout

Os códigos do seu projeto deve ficar dentro de um diretório reservado para o pacote/projeto.  
    
```
.
├── .gitignore
├── pyproject.toml
├── README.md
├── my_package/
│   ├── file0.py
│   ├── file1.py
│   ├── file2.py
│   └── ...
└── tests/
    ├── test0.py
    ├── test1.py
    └── ...
```

Em outras palavras, se você fosse escrever o primeiro arquivo do seu projeto e o nome do arquivo fosse `main.py`, ele deveria ser escrito em:  

```
<package_name>/main.py
```

No momento de distribuir a raiz é utilizada como referência para onde o pacote se encontra, então naturalmente iria incluir arquivos como `README.md`, `pyproject.toml`, etc.  

Nesse caso é necessário explicitamente dizer os arquivos ou diretórios a serem inclusos na distribuição (ou exclusos da distribuição).  