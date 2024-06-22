# Go

??? info "Compiled Language"

    Uma linguagem compilada é responsável por ler o código e gerar um binário.  
    
    Se a linguagem criar um binário chamado `main`, ele pode ser executado com:  
    
    === "Linux / Mac"
        
        ```
        ./main
        ```
    
    === "Windows"
        
        ```
        .\main
        ```

=== "Compile"
    
    Compila para um binário `main`:  
    
    ```
    go build main.go
    ```

=== "Compile & Execute"
    
    Compila e executa a saída da compilação:  
    
    ```
    go run main.go
    ```
    
    Nenhum binário é gerado.  

## Multiple Files (1)

Parecido com C, onde é necessário passar os arquivos a serem compilados.  

=== "Compile"
    
    Compila para um binário `main`:  
    
    ```
    go build main.go file0.go file1.go file2.go
    ```

=== "Compile & Execute"
    
    Compila e executa a saída da compilação:  
    
    ```
    go run main.go file0.go file1.go file2.go
    ```

Diferente de C, os arquivos a serem compilados (desta maneira) precisam estar no mesmo diretório.  

## Multiple Files (2)

A linguagem permite referenciar subpacotes do módulo, ou seja, se tratar seu projeto como um módulo então poderá importar código dos subdiretórios.  

=== "Before"

    ``` title="Project Layout"
    .
    ├── main.go
    └── file0.go
    ```
    
    ```go title="main.go"
    func main() {
        FooBar()
    }
    ```
    
    ```go title="file0.go"
    import "fmt"
    
    func FooBar() {
        fmt.Println("Hello World")
    }
    ```
    
    === "Compile"
        
        ```
        go build main.go file0.go
        ```
    
    === "Compile & Execute"
        
        ```
        go run main.go file0.go
        ```

=== "After"

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
        subpackage0.FooBar()
    }
    ```
    
    ```go title="file0.go"
    import "fmt"
    
    func FooBar() {
        fmt.Println("Hello World")
    }
    ```
    
    === "Compile"
        
        ```
        go build main.go
        ```
    
    === "Compile & Execute"
        
        ```
        go run main.go
        ```