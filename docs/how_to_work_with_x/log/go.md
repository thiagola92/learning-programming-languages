# Go

??? info "Official"

    Esta biblioteca é mantida pelos criadores oficiais da linguagem.

## File

```go
package main

import (
	"log"
	"os"
)

func main() {
	file, _ := os.OpenFile("example.log", os.O_CREATE|os.O_RDWR|os.O_APPEND, 0666)

	log.SetOutput(file)
	log.Print("Example")

	file.Close()
}
```

```
2024/09/23 04:42:09 Example
```

## Stderr

```go
package main

import (
	"log"
)

func main() {
	log.Print("Example")
}
```

```
2024/09/23 04:42:09 Example
```