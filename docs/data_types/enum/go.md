# Go

??? info "Adaptation"

    Esta linguagem possui uma adaptação do conceito.

## Enum

Enums são apenas nomes convertidos para número durante a compilação e podem ser fácilmente reproduzidos por definindo constantes com os valores desejados.  

=== "Set"

    ```go
    package main

    import "fmt"

    const (
        A = 0
        B = 1
        C = 2
    )

    func main() {
        fmt.Printf("A = %d\n", A)
        fmt.Printf("B = %d\n", B)
        fmt.Printf("C = %d\n", C)
    }
    ```

    ```
    A = 0
    B = 1
    C = 2
    ```

    !!! warning

        Ainda é uma declaração de constante e não uma definição de enum! Se você deixar de declarar os valores, ele irá utilizar o último valor para preencher os seguintes.  

        ```go
        const (
            A = 0
            B = 1
            C
        )
        ```

        ```
        A = 0
        B = 1
        C = 1
        ```

=== "Auto"

    A linguagem possui identificador que automaticamente se incrementa: `iota`.  

    ```go
    const (
        A = iota
        B
        C
    )
    ```

    Isto faz com que as constantes B e C também recebam o valor de `iota`, porém a cada uso terá crescido.  

    ```
    A = 0
    B = 1
    C = 2
    ```

    !!! note

        O valor de `iota` é resetado para zero sempre que a palavra reservada `const` aparece.  

        ```go
        const (
            A = iota
            B
            C
        )

        const D = iota
        ```

        ```
        A = 0
        B = 1
        C = 2
        D = 0
        ```
    
    !!! warning

        O valor de `iota` cresce mesmo sem ter sido utilizado naquela delcaração.  

        ```go
        const (
            A = iota
            B = 25
            C = iota
        )
        ```

        ```
        A = 0
        B = 25
        C = 2
        ```

=== "Both"

    ```go
    const (
        A = iota
        B = iota + 24
        C
    )
    ```

    ```
    A = 0
    B = 25
    C = 26
    ```