# Go

## Print

=== "Formatted"

    ```go
    package main

    import "fmt"

    func main() {
        fmt.Printf("%s\n", "example")
    }
    ```

=== "Raw"

    ```go
    package main

    import "os"

    func main() {
        os.Stdout.Write([]byte("example"))
    }
    ```

## Scan

=== "Formatted"

    ```go
    package main

    import "fmt"

    func main() {
        var text string
        fmt.Scanf("%s", &text)
    }
    ```

=== "Raw"

    ```go
    package main

    import (
        "bufio"
        "os"
    )

    func main() {
        text := make([]byte, 10)
        bufio.NewReader(os.Stdin).Read(text)
    }
    ```