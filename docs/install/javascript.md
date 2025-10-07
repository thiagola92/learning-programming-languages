# JavaScript

Por ser uma linguagem de script originalmente desenvolvida para navegadores, cada navegador implementava seu próprio interpretador para a linguagem ([V8 do Chrome](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)), [SpiderMonkey do Firefox](https://en.wikipedia.org/wiki/SpiderMonkey), [WebKit do Safari](https://en.wikipedia.org/wiki/WebKit)).  

Está parte do código dos navegadores responsável por executar a linguagem é conhecida como [JavaScript Engine](https://en.wikipedia.org/wiki/JavaScript_engine).  

*[interpretador]: Com o tempo adotou just-in-time compilation

Inicialmente era uma linguagem para ferramentas extenderem funcionalidades aos usuários de maneira prática. Porém com o tempo runtimes foram criados para permiterem a linguagem acessar a máquina do usuário da mesma forma que outras faziam, ou seja, deixou de só extender funcionalidades a uma ferramenta e passou a interagir diretamente com a máquina do usuário.  

Entre estes runtimes, podemos encontrar:

- [Node.js](https://en.wikipedia.org/wiki/Node.js)
- [Deno](https://en.wikipedia.org/wiki/Deno_(software))
- [Bun](https://en.wikipedia.org/wiki/Bun_(software))

A linguagem em si conta que você está executando o código no navegador mas estes runtimes fornecem bibliotecas para interação com o computador.  

**TLDR**: Não existe instalador oficial da linguagem. Utilize ela no navegador ou instale um runtime para executa-la localmente.  

## Node.js

=== "Oficial"

    Oficialmente a recomendação é instalar Node.js pelo [version manager](https://nodejs.org/en/download/package-manager) da linguagem.  

=== "Ubuntu"

    ```
    sudo apt install nodejs
    ```

## Deno

=== "Oficial"

    ```
    curl -fsSL https://deno.land/install.sh | sh
    ```

## Bun

=== "Oficial"

    ```
    curl -fsSL https://bun.sh/install | bash
    ```