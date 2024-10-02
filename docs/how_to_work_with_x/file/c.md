# C

## Read File

=== "Stream Content"

    ```C
    #include <stdio.h>

    int main() {
        char partial_content[10];

        FILE *file = fopen("example.txt", "r");
        fread(partial_content, 1, 9, file);
        fclose(file);
    }
    ```

## Write to File

=== "Stream Content"

    ```c
    #include <stdio.h>

    int main() {
        FILE *file = fopen("example.txt", "w");
        fwrite("Example", 1, 7, file);
        fclose(file);
    }
    ```