# Index

A ideia é reunir exemplos **básicos** de como trabalhar com um conhecimento genérico computação.  

Iremos ignorar tratamentos de erros pois, no contexto de exemplos, seria apenas encerrar o programa. Exemplo em Go:  

=== "Not Handling"

    ```go
    package main

    import "os"

    func main() {
        file, _ := os.OpenFile("example.txt", os.O_WRONLY, 0000)
        file.Write([]byte("Example"))
        file.Close()
    }
    ```

=== "Handling"

    ```go
    package main

    import "os"

    func main() {
        file, err := os.OpenFile("example.txt", os.O_WRONLY, 0000)

        if err != nil {
            os.Exit(1)
        }

        _, err := file.Write([]byte("Example"))

        if err != nil {
            os.Exit(2)
        }

        file.Close()

        if err != nil {
            os.Exit(3)
        }
    }
    ```

!!! warning

    Tratamento de erros é importante e não deve ser ignorado no dia-a-dia.  

## Print & Scan

Seção que fala sobre duas ações clássicas de se aprender em programação:  

- **Print**: Escrever um conteúdo na saída padrão (`stdout`)
- **Scan**: Ler um conteúdo na entrada padrão (`stdin`)

!!! note

    É bom saber que tudo lido e escrito são bytes, apenas dentro do seu programa que possuem um tipo específico.  

    - Formatted
        - **Print**: Transformamos uma devida variável em bytes para que ela seja exibida na tela
        - **Scan**: Definimos o tipo de variável a qual queremos que os bytes consumidos sejam convertidos
    - Raw
        - **Print & Scan**: Não existe nenhuma conversão, estamos lendo e escrevendo bytes
    - IO
        - **Print & Scan**: Mesmo que Raw porém utilizando `stdin`/`stdout` diretamente

## File

Seção que fala sobre as duas ações mais essenciais para arquivos:  

- **Read**: Ler o conteúdo de um arquivo
- **Write**: Escrever conteúdo em um arquivo

!!! note

    A saída e entrada padrão são arquivos, então podemos utilizar estes métodos para escrever na saída/entrada padrão.  

??? info "File Permissions"

    Arquivos possuem um controle de permissões básico para limitar como indíviduos podem utiliza-lo. Nove bits são utilizados para este controle:  

    ```
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    | bit 1 | bit 2 | bit 3 | bit 4 | bit 5 | bit 6 | bit 7 | bit 8 | bit 9 |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    ```

    Estes 9 bits são divididos entre 3 tipos de usuários, cada um com 3 bits que dizem o que eles podem fazer com aquele arquivo:  

    ```
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    |         owner         |         group         |        others         |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    | bit 1 | bit 2 | bit 3 | bit 4 | bit 5 | bit 6 | bit 7 | bit 8 | bit 9 |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    ```

    - **Owner**: É o atual dono do arquivo (não necessariamente quem criou o arquivo).  
    - **Group**: O seu computador pode ter diversos usuários (imagine um computador para a família inteira) e é possível categorizar todos juntos em um grupo para facilmente dar permissão do arquivo para eles. É importante eu ressaltar que um usuário pode estar em diversos grupos.    
    - **Others**: Qualquer usuário que não tenha caido dentro dos tipos acima.  

    O primeiro bit de cada tipo de usuário representa **read** e diz se aquele tipo de usuário pode ler o arquivo ou não. Se aquele bit estiver 1, então ele pode ler.  

    ```
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    |         owner         |         group         |        others         |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    | bit 1 | bit 2 | bit 3 | bit 4 | bit 5 | bit 6 | bit 7 | bit 8 | bit 9 |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    | READ  |       |       | READ  |       |       | READ  |       |       |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    ``` 

    O segundo bit de cada tipo de usuário representa **write** e diz se aquele tipo de usuário pode escrever no arquivo ou não. Se aquele bit estiver 1, então ele pode escrever.  

    ```
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    |         owner         |         group         |        others         |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    | bit 1 | bit 2 | bit 3 | bit 4 | bit 5 | bit 6 | bit 7 | bit 8 | bit 9 |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    | READ  | WRITE |       | READ  | WRITE |       | READ  | WRITE |       |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    ``` 

    O terceiro bit de cada tipo de usuário representa **execute** e diz se aquele tipo de usuário pode executar o arquivo ou não. Se aquele bit estiver 1, então ele pode executar.  

    ```
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    |         owner         |         group         |        others         |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    | bit 1 | bit 2 | bit 3 | bit 4 | bit 5 | bit 6 | bit 7 | bit 8 | bit 9 |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    | READ  | WRITE | EXEC  | READ  | WRITE | EXEC  | READ  | WRITE | EXEC  |
    +-------+-------+-------+-------+-------+-------+-------+-------+-------+
    ```

    Se eu te mostrasse os bits **`111 100 000`** você conseguiria notar que permissão cada tipo de usuário teria sobre o arquivo? (1)  
    { .annotate }  

    1.  **Owner** can read, write, execute  
        **Group** can read  
        **Others** can't do anything  
    
    É muito normal utilizar números na base 8 (octal) para representar essas permissões. O exemplo anterior seria escrito como **`740`** (1).  
    { .annotate }  

    1.  111 --> 7  
        100 --> 4  
        000 --> 0  

## Directory

Seção que fala sobre as ações mais comuns em um diretório:  

- **Create**: Criar um diretório
- **List**: Listar arquivos de um diretório
- **Remove**: Remover um diretório

??? info "Directory Permissions"

    > "Everything is a file"

    Diretórios são arquivos ([inodes](https://man7.org/linux/man-pages/man7/inode.7.html)) com informação de outros arquivos, única diferença é que uma abstração foi criada para você interagir com eles de forma segura.  

    Isto quer dizer que possui a mesma lógica de **File Permissions** vista na seção acima, tirando que pastas não podem ser executadas então o bit **execute** troca de significado para **search**.  

    ```
    +--------+--------+--------+--------+--------+--------+--------+--------+--------+
    |           owner          |           group          |          others          |
    +--------+--------+--------+--------+--------+--------+--------+--------+--------+
    | bit 1  | bit 2  | bit 3  | bit 4  | bit 5  | bit 6  | bit 7  | bit 8  | bit 9  |
    +--------+--------+--------+--------+--------+--------+--------+--------+--------+
    | READ   | WRITE  | SEARCH | READ   | WRITE  | SEARCH | READ   | WRITE  | SEARCH |
    +--------+--------+--------+--------+--------+--------+--------+--------+--------+
    ```

    O que cada combinação de permissões te deixa fazer:  

    - `---`: Não pode interagir com o diretório
    - `r--`: Permite descobrir os arquivos do diretório
        - `ls <directory>`
    - `-w-`: ???
    - `--x`: Permite acessar o diretório e subdiretórios
        - `cd <directory>`
        - `ls <directory>/<subdirectory>`
    - `rw-`: ???
    - `r-x`: Permite descobrir os arquivos do diretório e suas metadatas
        - `ls -l <directory>`
    - `-wx`: Permite modificar arquivos do diretório
        - `echo "example" > <directory>/file`
        - `touch <directory>/file`
        - `mv <directory>/file file`
        - `rm <directory>/file
        - `cp <directory>/file file2`
    - `rwx`: Permite tudo


## Memory

Seção que fala sobre como a linguagem se comporta em relação a armazenamento de dados na memória RAM ([heap](https://en.wikipedia.org/wiki/Memory_management#HEAP)).  

- Alocar
- Desalocar

## Process

- Fork
- Exec
- Spawn / Clone?

## Thread

## Network

- UDP
- TCP

## Log

Seção que fala sobre registrar eventos do seu programa (logs).  

Note que não existe regra de onde registrar estes eventos, nós poderiamos:

- **File**: Escreve-los em arquivos
- **Network**: Envia-los para servers
- **Stderr**: Escreve-los na saída de erro padrão

E poderiamos fazer em múltiplos deles ao mesmo tempo.  

??? info "Stdin, Stdout, Stderr"

    Por padrão programas possuem 3 fluxo de dados:

    - **stdin**: Entrada padrão
    - **stdout**: Saída padrão
    - **stderr**: Saída de erro padrão

    Em [Print & Scan](#print-scan) vimos comandos para interagir com `stdin` e `stdout`, porém logs são conhecidos por interagirem com `stderr`.  

    ```mermaid
    flowchart LR
        stdin[stdin]
        stdout[stdout]
        stderr[stderr]
        program((Program))

        stdin --> program
        program --> stdout
        program --> stderr
    ```
    
    Muitos programas utilizando `stdout` de um programa como `stdin` de outro programa para construir uma integração entre eles:  

    ```mermaid
    flowchart LR
        stdin[stdin]
        stdout[stdout]
        stderr[stderr]
        program((Program 1))

        stdin2[stdin]
        stdout2[stdout]
        stderr2[stderr]
        program2((Program 2))

        stdin --> program
        program --> stdout
        program --> stderr

        stdout --> stdin2
        stdin2 --> program2
        program2 --> stdout2
        program2 --> stderr2
    ```
    
    Consequentemente o `stderr` acaba sendo bom para escrever mensagens de logs, pois essa mensagens acabam não sendo enviadas para o próximo fluxo do programas.  
    
    !!! example

        [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) faz o link entre `stdout` de um programa com `stdin` de outro utilizando o operador `|`:  

        ```
        ls -l | grep "file.txt"
        ```  

## File Lock

Seção que fala sobre travas para arquivos.  

Basicamente existem dois tipos de travas:  

- **Shared lock**
    - Também conhecida como read lock
    - Diversos processos/threads podem possuir está trava ao mesmo tempo
    - É uma maneira de sinalizar que o arquivo está sendo utilizado para leitura mas nenhuma modificação vai acontecer nele
- **Exclusive lock**
    - Também conhecida como write lock
    - Apenas um processo/thread pode possuir está trava em um determinado tempo
    - É uma maneira de sinalizar que o arquivo pode estar sendo modificado e leitura dele pode trazer informações incorretas

??? info "Advisory Lock"

    Linux **não** implementa "Mandatory locking", ou seja, estas travas não proibem outros processos/threads de alterarem os arquivos.  

    Porém implementa "Advisory locks", ou seja, é uma cortesia dos processos/threads verificarem se o arquivo está travado ou não antes de acessa-lo.  

    Em outras palavras:

    | Process 1 | Process 2 | Result |
    | --------- | --------- | ------ |
    | Locks     | Locks     | 👍     |
    | Locks     | No Locks  | ❌     |
    | No Locks  | Locks     | ❌     |
    | No Locks  | No Locks  | ❌     |
