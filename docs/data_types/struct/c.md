# C

## Struct

```c
#include <stdio.h>

struct Example {
  int field1;
  float field2;
};

int main() {
  struct Example example;
  example.field1 = 1;
  example.field2 = 5.5;

  printf("example.field1 = %d\n", example.field1);
  printf("example.field2 = %f\n", example.field2);
}
```

```
example.field1 = 1
example.field2 = 5.500000
```