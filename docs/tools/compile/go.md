# Go

## Compile

=== "Compile"
    
    Compila para um executável `main`:  
    
    ```
    go build main.go
    ```

=== "Compile & Execute"
    
    Compila e executa a saída da compilação:  
    
    ```
    go run main.go
    ```
    
    Nenhum binário é gerado.  

## Compile when you have multiples files

Parecido com C, onde é necessário passar os arquivos a serem compilados.  

=== "Compile"
    
    Compila para um executável `main`:  
    
    ```
    go build main.go file0.go file1.go file2.go
    ```

=== "Compile & Execute"
    
    Compila e executa a saída da compilação:  
    
    ```
    go run main.go file0.go file1.go file2.go
    ```

Diferente de C, os arquivos a serem compilados (desta maneira) precisam estar no mesmo diretório.  

``` title="Project Layout"
.
├── main.go
└── file0.go
└── file1.go
└── file2.go
```

## Compile when you have files in subdirectories

!!! note
    
    Está parte conta que você tenha alguns conhecimentos de assuntos futuros.

A linguagem permite referenciar subpacotes do módulo, ou seja, se tratar seu projeto como um módulo então poderá importar código dos subdiretórios.  

``` title="Project Layout"
.
├── go.mod
├── main.go
└── subpackage0/
    └── file0.go
```

```go title="main.go"
import "my_module/subpackage0"

func main() {
    subpackage0.FooBar()    // Function from file0.go
}
```

=== "Compile"
    
    Compila para um executável `main`:  
    
    ```
    go build main.go
    ```

=== "Compile & Execute"
    
    Compila e executa a saída da compilação:  
    
    ```
    go run main.go
    ```