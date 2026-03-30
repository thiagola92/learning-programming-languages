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
    
    ```bash
    cargo build
    ```
    
    ??? note "Executable location"

        - Debug: `target/debug/<project_name>`
        - Release: `target/release/<project_name>`

=== "Compile & Execute"
    
    ```bash
    cargo run
    ```
    
    ??? note "Executable location"

        - Debug: `target/debug/<project_name>`
        - Release: `target/release/<project_name>`