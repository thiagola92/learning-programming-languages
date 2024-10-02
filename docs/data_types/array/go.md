# Go

## Array

=== "Empty"

    ```go
    package main

    import "fmt"

    var example [3]int

    func main() {
        fmt.Printf("example[0] = %d\n", example[0])
        fmt.Printf("example[1] = %d\n", example[1])
        fmt.Printf("example[2] = %d\n", example[2])
    }
    ```

    ```
    example[0] = 0
    example[1] = 0
    example[2] = 0
    ```

=== "Set"

    ```go
    package main

    import "fmt"

    var example = []int{1, 2, 3}

    func main() {
        fmt.Printf("example[0] = %d\n", example[0])
        fmt.Printf("example[1] = %d\n", example[1])
        fmt.Printf("example[2] = %d\n", example[2])
    }
    ```

    ```
    example[0] = 1
    example[1] = 2
    example[2] = 3
    ```

=== "Partial"

    ```go
    package main

    import "fmt"

    var example = [3]int{1, 2}

    func main() {
        fmt.Printf("example[0] = %d\n", example[0])
        fmt.Printf("example[1] = %d\n", example[1])
        fmt.Printf("example[2] = %d\n", example[2])
    }
    ```

    ```
    example[0] = 1
    example[1] = 2
    example[2] = 0
    ```

