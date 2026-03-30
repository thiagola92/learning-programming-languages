# Learning Programming Languages

Conjunto de informações básicas sobre diversas linguagens de programação.  

Idéia parecida com [Learn X in Y minutes](https://learnxinyminutes.com/).  

## Notes

- Caso não esteja citando o sistema operacional, assuma que é **Ubuntu**/**Fedora**.  
- Caso não esteja citando o shell, assuma que é **bash**.  
- Certas palavras podem vir em inglês por serem mais familiares para **mim**.  
    - Costumo botar título/seção em inglês.

## [Admonitions](https://zensical.org/docs/authoring/admonitions/)  
Sempre encolhidas para não prolongar o texto principal.  

??? note "Used to talk about curiosities"

    > Binário irá se encontrar na pasta `~/.local/bin`.  

??? abstract "Used at start of the page, to hold details about the page"

    > Adaptação da linguagem para este assunto.  

??? info "Used to teach about another subject"

    > Endianness se trata da ordem em que os bytes são ordenados (na máquina ou durante uma transmissão).  

??? tip "Used to give an advice"

    > Version managers ajudam caso vá trabalhar em diversos projetos em versões de linguagens diferentes.  

??? warning "Used to warn about problems that can happen if not careful"

    > Unions podem causar diversos problemas se não tomar cuidado.  

??? danger "Used to tell about problems that can happen"

    > Máquina pode parar de funcionar se instalar desta maneira.  

??? example "Used to show an example inside another admonition"

    Como o site é 99% exemplos, não faz sentido utilizar em todos exemplos.  

### How to use

```markdown
??? warn "Admonitions"

    A linha vazia acima é obrigatória!  
    O editor de texto não estava reconhecendo a sintáxe nos blocos de código sem ela.
```

## [Content Tabs](https://zensical.org/docs/authoring/content-tabs/)

### How to use
```markdown
=== Tab title

    A linha vazia acima é obrigatória!  
    O editor de texto não estava reconhecendo a sintáxe nos blocos de código sem ela.
```