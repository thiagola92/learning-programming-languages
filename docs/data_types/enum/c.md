# C

## Enum

=== "Auto"

    ```c
    #include <stdio.h>

    enum Example { A, B, C };

    int main() {
        printf("A = %d\n", A);
        printf("B = %d\n", B);
        printf("C = %d\n", C);
    }
    ```

    ```
    A = 0
    B = 1
    C = 2
    ```

=== "Set"

    ```c
    #include <stdbool.h>
    #include <stdio.h>

    enum Example {
        A = 0,
        B = 1,
        C = 2
    };

    int main() {
        printf("A = %d\n", A);
        printf("B = %d\n", B);
        printf("C = %d\n", C);
    }
    ```

    ```
    A = 0
    B = 1
    C = 2
    ```

=== "Both"

    ```c
    #include <stdbool.h>
    #include <stdio.h>

    enum Example {
        A,
        B = 25,
        C
    };

    int main() {
        printf("A = %d\n", A);
        printf("B = %d\n", B);
        printf("C = %d\n", C);
    }
    ```

    ```
    A = 0
    B = 25
    C = 26
    ```