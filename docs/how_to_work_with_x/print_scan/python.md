# Python

## Print

=== "Formatted"

    ```python
    print("{}".format("example"))
    ```

=== "Formatted 2"

    ```python
    string = "example"
    print(f"{string}")
    ```

=== "Raw"

    ```python
    print("example")
    ```

=== "IO"

    ```python
    import sys

    sys.stdout.write("example")
    ```

## Scan

=== "Raw"

    ```python
    string = input()
    ```

=== "IO"

    ```python
    import sys

    string = sys.stdin.read(30)
    ```

    !!! warning

        💀 Se a quantidade de bytes não for passada para `read()`, ele irá ler até a memória da máquina esgotar e travar.  

        Nunca bote sem limite quando se tratando da standard input (pois nunca tem fim).  