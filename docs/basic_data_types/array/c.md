# C

## Array

=== "Empty"

    ```c
    #include <stdio.h>

    int example[3];

    int main() {
        printf("example[0] = %d\n", example[0]);
        printf("example[1] = %d\n", example[1]);
        printf("example[2] = %d\n", example[2]);
    }
    ```

    ```
    example[0] = 0
    example[1] = 0
    example[2] = 0
    ```

=== "Set"

    ```c
    #include <stdio.h>

    int example[] = {1, 2, 3};

    int main() {
        printf("example[0] = %d\n", example[0]);
        printf("example[1] = %d\n", example[1]);
        printf("example[2] = %d\n", example[2]);
    }
    ```

    ```
    example[0] = 1
    example[1] = 2
    example[2] = 3
    ```

=== "Partial"

    ```c
    #include <stdio.h>

    int example[3] = {1, 2};

    int main() {
        printf("example[0] = %d\n", example[0]);
        printf("example[1] = %d\n", example[1]);
        printf("example[2] = %d\n", example[2]);
    }
    ```

    ```
    example[0] = 1
    example[1] = 2
    example[2] = 0
    ```

    !!! warning

        O array precisa ter espaço para receber todos os valores.  

        O seguinte irá gerar erro:  

        ```c
        int example[3] = {1, 2, 3, 4};
        ```