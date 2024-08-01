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

## File

- Read
- Write

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

## File Lock

Seção que fala sobre travas para arquivos.  

Basicamente existem dois tipos de travas:  

- Shared lock
    - Também conhecida como read lock
    - Diversos processos/threads podem possuir está trava ao mesmo tempo
    - É uma maneira de sinalizar que o arquivo está sendo utilizado para leitura mas nenhuma modificação vai acontecer nele
- Exclusive lock
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
    