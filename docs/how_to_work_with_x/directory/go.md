# Go

## Create file

=== "Regular file"

    ```go
    ```

=== "Directory"

    ```go
    package main

    import "os"

    func main() {
        os.Mkdir("example", 0660)
        os.Mkdir("example/subdir", 0660)
    }
    ```

## List files

## Remove file