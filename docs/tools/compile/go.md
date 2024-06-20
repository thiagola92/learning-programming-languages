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
    
    ```bash
    go build main.go
    ```

=== "Compile & Execute"
    
    Compila e executa a saída da compilação:  
    
    ```bash
    go run main.go
    ```
    
    Nenhum binário é gerado.  

## Multiple Files

Parecido com C, onde é necessário passar todos os arquivos a serem compilados.  

=== "Compile"
    
    Compila para um binário `main`:  
    
    ```bash
    go build main.go file0.go file1.go file2.go
    ```

=== "Compile & Execute"
    
    Compila e executa a saída da compilação:  
    
    ```bash
    go run main.go file0.go file1.go file2.go
    ```

Diferente de C, todos os arquivos a serem compilados precisam estar no mesmo diretório.  

Para utilizar subdiretórios, trate eles como [pacotes](/tools/package/go.md).  