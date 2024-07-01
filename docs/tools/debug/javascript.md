# JavaScript

??? info "Third Party"

    Este debugger não é mantido pelos criadores oficiais da linguagem.

Essa linguagem foi criada para ser executada no navegador, isto levou a diversos navegadores construiram seus próprios debuggers. Utilizando runtimes podemos linkar com os navegadores para eles debugarem o código.  

## Debug with Node.js

=== "Browser"

    ```
    node --inspect-brk main.js
    ```

=== "Built-in"

    ```
    node inspect main.js
    ```

## Debug with Deno

=== "Browser"

    ```
    deno run --inspect-brk main.js
    ```

## Debug with Bun

=== "Browser"

    ```
    bun --inspect-brk main.js
    ```