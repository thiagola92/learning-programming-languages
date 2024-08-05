# Go

## Print

=== "Formated"

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

=== "Formated"

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
        text := make([]byte, 30)

        reader := bufio.NewReader(os.Stdin)

        for i := 0; i < len(text); i++ {
            b, _ := reader.ReadByte()
            text[i] = b
        }
    }
    ```