# C

## Union

```c
#include <stdio.h>

union Example {
  int field1;
  float field2;
};

int main() {
  union Example example;

  example.field1 = 1;
  printf("example.field1 = %d\n", example.field1);
  printf("example.field2 = %f\n\n", example.field2);

  example.field2 = 5.5;
  printf("example.field1 = %d\n", example.field1);
  printf("example.field2 = %f\n", example.field2);
}
```

```
example.field1 = 1
example.field2 = 0.000000

example.field1 = 1085276160
example.field2 = 5.500000
```