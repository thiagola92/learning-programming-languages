# Go

## Create directory

```go
package main

import "os"

func main() {
    os.Mkdir("example", 0777)
}
```

## List files

=== "All Content"

    ```go
    package main

    import "os"

    func main() {
        files, _ := os.ReadDir("example")

        for _, file := range files {
            println(file.Name())
        }
    }
    ```

=== "Stream Content"

    ```go
    package main

    import "os"

    func main() {
        dir, _ := os.Open("example")
        files, _ := dir.ReadDir(10) // Read ten records.

        for _, file := range files {
            println(file.Name())
        }

        dir.Close()
    }
    ```

=== "Stream Content 2"

    ```go
    package main

    import "os"

    func main() {
        dir, _ := os.OpenFile("example", os.O_RDONLY, 0000)
        files, _ := dir.ReadDir(10) // Read ten records.

        for _, file := range files {
            println(file.Name())
        }

        dir.Close()
    }
    ```

## Remove directory

```go
package main

import "os"

func main() {
    os.Remove("example")
}
```