# Python

??? info "Third Party"

    Este gerenciador de pacotes não é mantido pelos criadores oficiais da linguagem.

A linguagem recomenda a utilização do [Pip](https://pip.pypa.io/en/stable/).  

## Add with Pip

```
pip install <package_name>
```

!!! warning

    Pip não armazena suas dependências automaticamentes em um arquivo do seu projeto, então é necessário criar o arquivo de dependências manualmente.  

    O comando `pip freeze` é utilizado para listar as dependências instaladas até o momento.  
    
    Utilizando o seguinte prompt podemos criar/atualizar o arquivo de dependências (normalmente chamado de `requirements.txt`):  

    ```
    pip freeze > requirements.txt
    ```

## Add with PDM

```
pdm add <package_name>
```