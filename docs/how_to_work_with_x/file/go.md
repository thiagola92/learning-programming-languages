# Go

## Read File

=== "All Content"

    ```go
    package main

    import "os"

    func main() {
        content, _ := os.ReadFile("example.txt")
    }
    ```

=== "Stream Content"

    ```go
    package main

    import "os"

    func main() {
        partial_content := make([]byte, 10)

        file, _ := os.OpenFile("example.txt", os.O_RDONLY, 0000)
        file.Read(partial_content)
        file.Close()
    }
    ```

## Write to File

=== "All Content"

    ```go
    package main

    import "os"

    func main() {
	    os.WriteFile("example.txt", []byte("Example"), 0600)
    }
    ```

=== "Stream Content"

    ```go
    package main

    import "os"

    func main() {
        file, _ := os.OpenFile("example.txt", os.O_WRONLY, 0000)
        file.Write([]byte("Example"))
        file.Close()
    }
    ```