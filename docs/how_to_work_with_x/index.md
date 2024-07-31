# Index

A ideia é reunir exemplos **básicos** de como trabalhar com um conhecimento genérico computação.  

Iremos ignorar tratamentos de erros pois, no contexto de exemplos, seria apenas encerrar o programa. Por exemplo:  

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

## Lock