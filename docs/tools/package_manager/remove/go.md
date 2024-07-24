# Go

??? info "Official"

    Este gerenciador de pacotes é mantido pelos criadores oficiais da linguagem.

## Remove

Remova qualquer importe de um especifico pacote do seu código.  

Execute o seguinte comando para que o seu código seja analisado e as dependências **não** necessárias sejam removidas.  

```
go mod tidy
```

## Alternative

Remove a dependência.  

```
go get <path>@none
```

Normalmente é o número da versão que se deve botar após o `@`, porém ao botar `none` o comando entende que é para remover o pacote.  