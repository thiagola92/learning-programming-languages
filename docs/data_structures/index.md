# Index

!!! note

    Está é uma lista de estruturas interessantes para mim.  
    
    Para uma lista mais completa visite: https://en.wikipedia.org/wiki/List_of_data_structures  

## Tagged Union

```
tagged union {
    type
    value
}
```

## Slice

```
slice {
    address
    size
}
```

## List

*(Linked List)*

```
list {
    value
    next
}
```

## Stack

### List

```
stack {
    value
    next
}
```

### Array

```
stack {
    array
    current
    max
}
```

## Queue

### List

```
queue {
    first {
        value
        next
    }
    last {
        value
        next
    }
}
```

### Array

Necessário fazer shift a cada operação de remoção da fila.  

```
queue {
    array
    last
    max
}
```

Iniciando do meio não é preciso fazer operação de shift ao menos que um dos cantos chegue à metade do máximo.  

```
queue {
    array
    first
    last
    max
}
```

## Hash Map

*(Map, Hash Table, Associative Array)*

## Tree

```
tree {
    left
    value
    right
}
```