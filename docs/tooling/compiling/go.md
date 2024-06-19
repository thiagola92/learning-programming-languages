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