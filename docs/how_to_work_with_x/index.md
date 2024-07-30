# Index

A ideia é reunir exemplos **básicos** de como trabalhar com um conhecimento genérico computação.  

Existe diversas maneiras das quais podemos interagir com arquivos (criar, truncar, deletar, ler, escrever, renomear, ...). No entanto, é mais fácil mostrar exemplos de interações essenciais (ler, escrever) e o desenvolvedor utiliza-las como base temporária enquanto não deseja se aprofundar na linguagem.  

Por exemplo, na linguagem [Go](https://go.dev/) podemos escrever em um arquivo existente com:  

```go
package main

import "os"

func main() {
    file, _ := os.OpenFile("example.txt", os.O_WRONLY, 0000)
    quantity, _ := file.Write([]byte("Example"))
    file.Close()
}
```

Se o desenvolvedor quisesse que o arquivo também fosse criado caso não existisse, ele poderia olhar na documentação oficial do pacote `os` ou da função `OpenFile()`.  

Note que ignoramos tratamentos de erro, pois buscamos passar o mais rápido o conhecimento sobre aquele determinado assunto. Além disto, tratamentos de erros em exemplos acabariam tratando com o encerramento do programa, o que não seria nada de especial para o leitor.  

## File

## Directory

## Process

## Thread

## Network

## Lock