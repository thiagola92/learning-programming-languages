# Python

## Read File

=== "All Content"

    ```python
    file = open("example.txt", "r")
    content = file.read()
    file.close()
    ```

=== "All Content 2"

    ```python
    with open("example.txt", "r") as file:
        content = file.read()
    ```

=== "All Content 3"

    ```python
    from pathlib import Path

    content = Path("example.txt").read_text()
    ```

=== "Stream Content"

    ```python
    file = open("example.txt", "r")
    partial_content = file.read(30)
    file.close()
    ```

=== "Stream Content 2"

    ```python
    with open("example.txt", "r") as file:
        partial_content = file.read(30)
    ```

## Write to File

=== "All Content"

    ```python
    from pathlib import Path

    Path("example.txt").write_text("Example")
    ```

=== "Stream Content"

    ```python
    file = open("example.txt", "w")
    file.write("Example")
    file.close()
    ```

=== "Stream Content 2"

    ```python
    with open("example.txt", "w") as file:
        file.write("Example")
    ```