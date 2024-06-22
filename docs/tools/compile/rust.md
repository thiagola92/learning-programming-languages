# Rust

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
    rustc main.rs
    ```

## Package Manager

O package manager da linguagem fornece atalhos para compilar e executar, porém isto envolve certas configurações do package manager.  

=== "Compile"
    
    Compila para um binário localizado em `target/debug/<project_name>`:  
    
    ```bash
    cargo build
    ```
    
    !!! note
    
        Compila para `target/release/<project_name>` se for release.

=== "Compile & Execute"
    
    Compila para um binário localizado em `target/debug/<project_name>` e o executa:  
    
    ```bash
    cargo run
    ```
    
    !!! note
    
        Compila para `target/release/<project_name>` se for release.