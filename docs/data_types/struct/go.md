# Go

## Struct

```go
package main

import "fmt"

type Example struct {
	field1 int
	field2 float32
}

func main() {
	var example Example
	example.field1 = 1
	example.field2 = 5.5

	fmt.Printf("example.field1 = %d\n", example.field1)
	fmt.Printf("example.field2 = %f\n", example.field2)
}
```

```
example.field1 = 1
example.field2 = 5.500000
```