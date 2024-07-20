# Index

## Compile

Seção que fala sobre compilar/executar o código da linguagem.  

Essa seção inclui linguagens que compilam, interpretam ou ambos. Normalmente:  

- Compilar envolve gerar um executável para uma determinada arquitetura de máquina.  
- Interpretar envolve ler o código e ao mesmo tempo executar o código lido.  

Mas os dois não são excludentes, pois é possível compilar parcialmente ou compilar enquanto está lendo o código.  

Então não se apegue a detalhes, o foco é executar a linguagem.  

!!! note

    Em casos de compilação, pode ser necessário executar o executável manualmente. Exemplo:  
    
    === "Linux / Mac"
        
        ```
        ./main
        ```
    
    === "Windows"
        
        ```
        .\main
        ```

## Format

Seção que fala sobre o formatador da linguagem.  

Formatadores alteram o código para seguir certos padrões de escrita, porém sem alterar o comportamento quando executado.  

## Debug

Seção que fala sobre o debugger da linguagem.  

Debuggers permitem os programadores acompanharem a execução de um código a fim de análisar ou descobrir erros.  

!!! note

    Nem todas as linguagens possuem um debugger próprio, algumas recomendam utilizar debuggers já existentes ou criados pela comunidade. Por exemplo, é possível usar [GDB](https://en.wikipedia.org/wiki/GNU_Debugger) e [LLDB](https://en.wikipedia.org/wiki/LLDB_(debugger)) com a linguagem Rust.  
    
    *[GDB]: GNU Debugger
    *[LLDB]: Low-Level Debugger

## LSP

## Package Manager

Seção que fala sobre o gerenciador de pacotes da linguagem.  

Gerenciadores de pacotes mantém uma lista de módulos/pacotes/bibliotecas a serem importados para o seu projeto.  

!!! note

    Existem 3 termos utilizados quando estamos falando de código a ser importado por outros:  

    - Módulo: Arquivo contendo código
    - Pacote: Conjunto de módulos dentro do mesmo diretório
    - Biblioteca: Conjunto de pacotes e módulos

## Version Manager

Seção que fala sobre gerenciador de versão para a linguagem.  

Gerenciadores de versão permitem a alteração da versão da linguagem dentro da máquina do desenvolvedor.  