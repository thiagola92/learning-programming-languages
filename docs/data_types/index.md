# Index

## Char

*(Character)*

A idéia de um caracter é representar um [grafema](https://www.dicio.com.br/grafema/) (unidade mínima de um sistema de escrita). O que não é fácil quando lidando com diversos idiomas.  

Atualmente UTF-8 é encode mais recomendado por conseguir representar um grafema de diversas linguagens, ele pode ocupar de 1 até 4 bytes dependendo de qual lingua o caracter pertencer.  

Recomendação de video: https://www.youtube.com/watch?v=ut74oHojxqo  

!!! note

    Atualmente é muito comum assumir que um char é 1 byte (8 bits) pois foi o padrão adotado por um longo periodo de tempo (ASCII).  
    
    Mas durante o tempo de vida dos computadores, byte não foi sempre a medida mínima de memória, já tivemos diversos tamanhos de bits e eles também possuiam o conceito de caracteres.  

    Tivemos 6 bits, 5 bits, 4 bits... Até o famoso padrão de encode ASCII começou como 7 bits e foi adaptado para 8 bits.  

## Int

*(Integer)*

## Float

*(Floating Point)*

## Enum

*(Enumerated)*

```
enum {
    value 1
    value 2
    value 3
}
```

## Array

## Union

```
union {
    option 1
    option 2
    option 3
}
```

## Struct

*(Record)*

```
struct {
    field 1
    field 2
    field 3
}
```