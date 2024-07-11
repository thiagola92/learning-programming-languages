# Rust

??? info "Imposed"

    A linguagem apenas aceita importar código de arquivos que seguiram a regra da linguagem. Por exemplo:  
    
    > "Apenas arquivos no mesmo diretório"  
    > "Apenas arquivos em subdiretórios"  
    > "Apenas em diretórios que tenham o arquivo `.package"  

A convenção é deixar os códigos do seu projeto dentro do diretório `src`, porém isto é opcional.  

## Modules

Todos os módulos utilizados pelo arquivo contendo a função `main()` precisam estar no mesmo level que ele.  

```
.
├── .gitignore
├── Cargo.toml
├── README.md
└── src/
    ├── file0.rs
    ├── file1.rs
    └── ...
```

## Submodules

Módulos podem possuir outros módulos, porém eles vão precisar estar localizados em um diretório com o nome do módulo pai.  

```
.
├── .gitignore
├── Cargo.toml
├── README.md
└── src/
    ├── file0.rs
    ├── file1.rs
    ├── ...
    └── file1/
        ├── file2.rs
        ├── file3.rs
        └── ...
```

Essa lógica se extende adiante, ou seja, se o módulo `file2` possuir módulos, eles precisam estar dentro de um diretório chamado `file2`.  

```
.
├── .gitignore
├── Cargo.toml
├── README.md
└── src/
    ├── file0.rs
    ├── file1.rs
    ├── ...
    └── file1/
        ├── file2.rs
        ├── file3.rs
        ├── ...
        └── file2/
            └── ...
```