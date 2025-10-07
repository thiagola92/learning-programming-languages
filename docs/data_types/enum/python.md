# Python

??? abstract "Adaptation"

    Esta linguagem possui uma adaptação do conceito.

## Enum

A linguagem utiliza outra classe (`Enum`) para ajudar a reproduzir o comportamento de um enum.  

=== "Set"

    ```python
    from enum import Enum

    class Example(Enum):
        A = 0
        B = 1
        C = 2

    print(f"A = {Example.A}")
    print(f"B = {Example.B}")
    print(f"C = {Example.C}")
    ```

    ```
    A = Example.A
    B = Example.B
    C = Example.C
    ```

=== "Auto"

    ```python
    from enum import Enum, auto

    class Example(Enum):
        A = auto()
        B = auto()
        C = auto()

    print(f"A = {Example.A}")
    print(f"B = {Example.B}")
    print(f"C = {Example.C}")
    ```

    ```
    A = Example.A
    B = Example.B
    C = Example.C
    ```