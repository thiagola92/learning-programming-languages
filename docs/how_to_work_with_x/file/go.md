# Go

## Write to File

=== "All Content"

    ```go
    package main

    import "os"

    func main() {
	    err := os.WriteFile("example.txt", []byte("Example"), 0600)
    }
    ```

=== "Stream Content"

    ```go
    package main

    import "os"

    func main() {
        file, err := os.OpenFile("example.txt", os.O_WRONLY, 0000)
        quantity, err := file.Write([]byte("Example"))
        file.Close()
    }
    ```

## Read File

=== "All Content"

    ```go
    package main

    import "os"

    func main() {
        content, err := os.ReadFile("example.txt")
    }
    ```

=== "Stream Content"

    ```go
    package main

    import "os"

    func main() {
        partial_content := make([]byte, 10)

        file, err := os.OpenFile("example.txt", os.O_RDONLY, 0000)
        quantity, err := file.Read(partial_content)
        file.Close()
    }
    ```