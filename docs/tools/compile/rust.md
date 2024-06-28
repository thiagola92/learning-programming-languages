# Rust

## Compile

=== "Compile"
    
    Compila para um executável `main`:  
    
    ```bash
    rustc main.rs
    ```

## Compile with package manager

O package manager da linguagem fornece atalhos para compilar e executar, porém isto envolve o diretório estar configurado para o package manager.  

=== "Compile"
    
    Compila para um executável localizado em `target/debug/<project_name>`:  
    
    ```bash
    cargo build
    ```
    
    !!! note
    
        Compila para `target/release/<project_name>` se for release.

=== "Compile & Execute"
    
    Compila para um executável localizado em `target/debug/<project_name>` e o executa:  
    
    ```bash
    cargo run
    ```
    
    !!! note
    
        Compila para `target/release/<project_name>` se for release.