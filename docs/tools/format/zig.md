# Zig

??? abstract "Official"

    Este formatador é mantido pelos criadores oficiais da linguagem.

## Format

Caso o argumento seja um arquivo, apenas aquele arquivo será formatado.

```
zig fmt main.zig
```

Caso o argumento seja um diretório, aplica o comando em todos os arquivos e diretórios (causando recursão).

```
zig fmt .
```