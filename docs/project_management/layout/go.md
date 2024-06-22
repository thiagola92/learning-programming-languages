# Go

??? note "Imposed"

    A linguagem obriga a seguir o layout.

Todos os arquivos relacionados ao mesmo pacote devem ficar na mesma pasta e o pacote principal deve ficar na raiz do projeto.  

```
.
├── .gitignore
├── go.mod
├── README.md
├── file0.go
├── file1.go
├── file2.go
└── ...
```

Desta forma outros podem importar seu módulo com o URL do repositório. Por exemplo:  

```go
import "https://www.github.com/username/repository"
```

## Sub-package

É normal dividir um projeto grande em subdiretórios, nesse caso cada subdiretório é considerado um subpacote.  

```
.
├── .gitignore
├── go.mod
├── README.md
├── file0.go
├── file1.go
├── file2.go
├── ...
├── subpackage0/
│   ├── file3.go
│   ├── file4.go
│   └── ...
└── subpackage1/
    ├── file5.go
    ├── file6.go
    └── ...
```

Exemplo de como importar código de subpacotes:  

```go
import (
    "https://www.github.com/username/repository/subpackage0"
    "https://www.github.com/username/repository/subpackage1"
)
```

O arquivo `go.mod` apenas existe no pacote principal pois ele define o início de um módulo (um conjunto de pacotes que existem para se complementar).  

## Private

Diretório `internal` é especial pois a linguagem não permite que outros módulos importem dele.  

```
.
├── .gitignore
├── go.mod
├── README.md
├── file0.go          # Can be imported ✔️
├── subpackage0/      # Can be imported ✔️
│   └── file0.go      # Can be imported ✔️
└── internal/
    ├── file1.go      # Cannot be imported ❌
    └── subpackage1/  # Cannot be imported ❌
        └── file2.go  # Cannot be imported ❌
```

Ele é utilizado para armazenar código o qual o usuário não deve interagir.  