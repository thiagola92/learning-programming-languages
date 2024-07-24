# Go

??? info "Official"

    Este gerenciador de pacotes é mantido pelos criadores oficiais da linguagem.

## Add

Declare o importe do pacote a ser utilizado no seu código.  

```go
import "<path>"
```

Execute o seguinte comando para que o seu código seja analisado e as dependências necessárias sejam adicionadas.  

```
go mod tidy
```

## Alternative

Adiciona a dependência.  

```
go get <path>
```