# C

## Print

=== "Formated"

    ```c
    #include <stdio.h>

    int main() {
        printf("%s\n", "example");
    }
    ```

## Scan

=== "Formated"

    ```c
    #include <stdio.h>

    int main() {
        char string[100];
        scanf("%s", string);
    }
    ```

!!! note

    Importante saber que `scanf()` utiliza caracteres brancos (espaço, tab, newline, etc) para determinar o fim do scan de um elemento.  

    Em outras palavras, se o input para `scanf("%s", string)` for "Hello world", apenas o "Hello" será armazenado em `string`.