# C

## Create directory

```c
#include <sys/stat.h>

int main() {
  mkdir("example", 0777);
}
```

## List files

=== "Stream Content"

    ```c
    #include <dirent.h>
    #include <stdio.h>

    int main() {
        DIR *dir = opendir("example");
        struct dirent *directory_entry = readdir(dir);

        while (directory_entry != NULL) {
            printf("%s\n", directory_entry->d_name);
            directory_entry = readdir(dir);
        }

        closedir(dir);
    }
    ```

## Remove directory

```c
#include <unistd.h>

int main() {
  rmdir("example");
}
```