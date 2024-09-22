# Index

A ideia é reunir exemplos **básicos** de como trabalhar com um conhecimento genérico computação.  

Iremos ignorar tratamentos de erros pois, no contexto de exemplos, seria apenas encerrar o programa. Exemplo em Go:  

=== "Not Handling"

    ```go
    package main

    import "os"

    func main() {
        file, _ := os.OpenFile("example.txt", os.O_WRONLY, 0000)
        file.Write([]byte("Example"))
        file.Close()
    }
    ```

=== "Handling"

    ```go
    package main

    import "os"

    func main() {
        file, err := os.OpenFile("example.txt", os.O_WRONLY, 0000)

        if err != nil {
            os.Exit(1)
        }

        _, err := file.Write([]byte("Example"))

        if err != nil {
            os.Exit(2)
        }

        file.Close()

        if err != nil {
            os.Exit(3)
        }
    }
    ```

!!! warning

    Tratamento de erros é importante e não deve ser ignorado no dia-a-dia.  

## Print & Scan

Seção que fala sobre duas ações clássicas de se aprender em programação:  

- **Print**: Escrever um conteúdo na saída padrão (`stdout`)
- **Scan**: Ler um conteúdo na entrada padrão (`stdin`)

!!! info

    É importante entender que a princípio tudo lido e escrito são bytes, apenas dentro do seu programa que possuem um tipo específico.  

    - Formatted
        - **Print**: Transformamos uma devida variável em bytes para que ela seja exibida na tela
        - **Scan**: Definimos o tipo de variável a qual queremos que os bytes consumidos sejam convertidos
    - Raw
        - **Print & Scan**: Não existe nenhuma conversão, estamos lendo e escrevendo bytes
    - IO
        - **Print & Scan**: Mesmo que Raw porém utilizando `stdin`/`stdout` diretamente

## File

Seção que fala sobre as duas ações mais essenciais para arquivos:  

- **Read**: Ler o conteúdo de um arquivo
- **Write**: Escrever conteúdo em um arquivo

!!! note

    No linux a saída e entrada padrão são arquivos, então pode se utilizar estes métodos para escrever na saída/entrada padrão.  

## Directory

- List
- Create

## Process

- Fork
- Exec
- Spawn / Clone?

## Thread

## Network

- UDP
- TCP

## Log

Seção que fala sobre registrar eventos do seu programa (logs).  

Note que não existe regra de onde registrar estes eventos, nós poderiamos:

- **File**: Escreve-los em arquivos
- **Network**: Envia-los para servers
- **Stderr**: Escreve-los na saída de erro padrão

E poderiamos fazer em múltiplos deles ao mesmo tempo.  

!!! info

    Por padrão programas possuem 3 fluxo de dados:

    - **stdin**: Entrada padrão
    - **stdout**: Saída padrão
    - **stderr**: Saída de erro padrão

    Em [Print & Scan](#print-scan) vimos comandos para interagir com `stdin` e `stdout`, porém logs são conhecidos por interagirem com `stderr`.  

    ```mermaid
    flowchart LR
        stdin[stdin]
        stdout[stdout]
        stderr[stderr]
        program((Program))

        stdin --> program
        program --> stdout
        program --> stderr
    ```
    
    Muitos programas utilizando `stdout` de um programa como `stdin` de outro programa para construir uma integração entre eles:  

    ```mermaid
    flowchart LR
        stdin[stdin]
        stdout[stdout]
        stderr[stderr]
        program((Program 1))

        stdin2[stdin]
        stdout2[stdout]
        stderr2[stderr]
        program2((Program 2))

        stdin --> program
        program --> stdout
        program --> stderr

        stdout --> stdin2
        stdin2 --> program2
        program2 --> stdout2
        program2 --> stderr2
    ```
    
    Consequentemente o `stderr` acaba sendo bom para escrever mensagens de logs, pois essa mensagens acabam não sendo enviadas para o próximo fluxo do programas.  
    
    !!! example

        [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) faz o link entre `stdout` de um programa com `stdin` de outro utilizando o operador `|`:  

        ```
        ls -l | grep "file.txt"
        ```  

## File Lock

Seção que fala sobre travas para arquivos.  

Basicamente existem dois tipos de travas:  

- **Shared lock**
    - Também conhecida como read lock
    - Diversos processos/threads podem possuir está trava ao mesmo tempo
    - É uma maneira de sinalizar que o arquivo está sendo utilizado para leitura mas nenhuma modificação vai acontecer nele
- **Exclusive lock**
    - Também conhecida como write lock
    - Apenas um processo/thread pode possuir está trava em um determinado tempo
    - É uma maneira de sinalizar que o arquivo pode estar sendo modificado e leitura dele pode trazer informações incorretas

!!! warning

    Linux **não** implementa "Mandatory locking", ou seja, estas travas não proibem outros processos/threads de alterarem os arquivos.  

    Linux implementa "Advisory locks", ou seja, é uma cortesia dos processos/threads verificarem se o arquivo está travado ou não antes de acessa-lo.  

    Em outras palavras:

    | Process 1 | Process 2 | Result |
    | --------- | --------- | ------ |
    | Locks     | Locks     | 👍     |
    | Locks     | No Locks  | ❌     |
    | No Locks  | Locks     | ❌     |
    | No Locks  | No Locks  | ❌     |