# Python

## Create directory

=== "1"

    ```python
    import os

    os.mkdir("example")
    ```

=== "2"

    ```python
    from pathlib import Path

    Path("example").mkdir()
    ```

## List files

=== "All Content"

    ```python
    import os

    files = os.listdir("example")

    for file in files:
        print(file)
    ```

=== "Stream Content"

    ```python
    from pathlib import Path

    files = Path("example").iterdir()

    for file in files:
        print(file)
    ```

## Remove directory

=== "1"

    ```python
    import os

    os.rmdir("example")
    ```

=== "2"

    ```python
    from pathlib import Path

    Path("example").rmdir()
    ```