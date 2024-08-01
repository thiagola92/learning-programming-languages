# Go

??? info "Third Party"

    Esta funcionalidade não é mantido pelos criadores oficiais da linguagem.

Embora a linguagem internamente possua essa [funcionalidade](https://pkg.go.dev/cmd/go/internal/lockedfile), ela não está disponível para os desenvolvedores.  

Uma alternativa é utilizar o pacote [go-internal](https://pkg.go.dev/github.com/rogpeppe/go-internal) que disponibiliza alguns pacotes internos para o nosso uso.

## Shared Lock

=== "All Content"

    ```go
    package main

    import (
        "github.com/rogpeppe/go-internal/lockedfile"
    )

    func main() {
        content, _ := lockedfile.Read("example.txt")
    }
    ```

=== "Stream Content"

    ```go
    package main

    import (
        "github.com/rogpeppe/go-internal/lockedfile"
    )

    func main() {
        file, _ := lockedfile.Open("example.txt")
        // ...
        file.Close()
    }
    ```

## Exclusive Lock

=== "All Content"

    ```go
    package main

    import (
        "github.com/rogpeppe/go-internal/lockedfile"
    )

    func main() {
        lockedfile.Write("example.txt", []byte("Example"), 0600)
    }
    ```

=== "Stream Content"

    ```go
    package main

    import (
        "github.com/rogpeppe/go-internal/lockedfile"
    )

    func main() {
        file, _ := lockedfile.Edit("example.txt")
        // ...
        file.Close()
    }
    ```