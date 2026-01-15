# Index

## Bool

*(Boolean)*

Representação de verdadeiro e falso, porém por não ser possível armazenar 1 bit sozinho, ele ocupa sempre o espaço mínimo de 1 byte.  

## Int

*(Integer)*

Representação de um [número inteiro](https://pt.wikipedia.org/wiki/N%C3%BAmero_inteiro), quantidade de números que é possível representar depende da quantidade de bytes utilizados.  

## Float

*(Floating Point)*

Representação de um [número racional](https://pt.wikipedia.org/wiki/N%C3%BAmero_racional), quantidade de números que é possível representar depende da quantidade de bytes utilizados.  

## Char

*(Character)*

A idéia de um caracter é representar um [grafema](https://www.dicio.com.br/grafema/) (unidade mínima de um sistema de escrita). O que não é fácil quando lidando com diversos idiomas.  

Atualmente UTF-8 é encode mais recomendado por conseguir representar um grafema de diversas linguagens, ele pode ocupar de 1 até 4 bytes dependendo de qual lingua o caracter pertencer.  

Recomendação de video: [https://www.youtube.com/watch?v=ut74oHojxqo](https://www.youtube.com/watch?v=ut74oHojxqo)  

??? info "Size of a byte"

    Atualmente é muito comum assumir que um char é 1 byte (8 bits) pois foi o padrão adotado por um longo periodo de tempo (ASCII).  
    
    Mas durante o tempo de vida dos computadores, 8 bits não foi sempre a medida mínima de memória, já tivemos diversos tamanhos e eles também eram usados para representar caracteres.  

    Tivemos 6 bits, 5 bits, 4 bits... Até o famoso padrão de encode ASCII começou como 7 bits e foi adaptado para 8 bits.  

## Enum

*(Enumerated)*

Maneira de dar nomes a valores constantes para facilitar a escrita e entendimento do código. Durante a compilação estes nomes são convertidos para os devidos valores.  

```
enum {
    name1
    name2
    name3
}
```

## Array

Coleção de dados que possuem o mesmo tipo e são armazenados sequêncialmente na memória.  

É possível caminhar pelos valores do array dando um "passo" na memória. O tamanho do passo é relativo ao tipo do dado armazenado, ou seja, um array de inteiros de 4 bytes fará com que o passo passe 4 endereços de memória.  

Não é possível alterar o tamanho de um array pois não existe garantia que o espaço seguinte da memória está livre para ser adicionado ao array. A solução é requisitar um novo espaço de memória com espaço suficiente e copiar os valores.  

```
array {
    value1
    value2
    value3
}
```

## Union

Permite utilizar um espaço de memória para armazenar um entre vários tipos de dados.  

O tamanho do espaço de memória terá que ser o maior dentro dos tipos.  

```
union {
    type1
    type2
    type3
}
```

!!! warning

    É importante notar que é perigoso não saber o tipo da variável naquele exato momento, pois tipos diferentes de variáveis possuem organização diferente na memória e operam de maneira diferente no processador.  
    
    Por exemplo, nenhuma das operações abaixo irá funcionar pois armazenamos na memória o valor 10 da maneira esperada por `int`, porém em todos os casos tentamos utilizar aquele espaço de memória como se tivesse um `float`.  

    ```c
    #include <stdio.h>

    union Example {
        int field1;
        float field2;
    };

    int main() {
        union Example example;

        example.field1 = 10;
        printf("result = %d\n", example.field2 + 1);
        printf("result = %d\n", example.field2 + 1.5);
        printf("result = %f\n", example.field2 + 1);
        printf("result = %f\n", example.field2 + 1.5);
    }
    ```

    Não importa se tentarmos exibir o valor como se ele fosse um `int` (`%d`) ou `float` (`%f`) pois o calculo foi feito pensando que o campo de memória tinha um float, então o resultado se tornou lixo.  

    ```
    result = -48637544
    result = -2103905632
    result = 1.000000
    result = 1.500000
    ```

    [Tagged union](https://en.wikipedia.org/wiki/Tagged_union) é uma estrutura de dados utilizada para evitar este tipo de problema.  

## Struct

*(Record)*

É um tipo de dado composto por outros tipos de dados.  

O espaço de memória ocupado pela struct é a soma de cada tipo que a compõe (ignorando fatores como [data alignment](https://en.wikipedia.org/wiki/Data_structure_alignment)).  

```
struct {
    field1
    field2
    field3
}
```

??? info "Class"

    Considero structs em esteroide, pois possuem o mesmo conceito de armazenar diversos tipos de dados em conjunto porém adicionam outras ideias como: herança, encapsulamento, ...  

    Algumas linguagens conseguem reproduzir parte do comportamento de classes:  

    ??? example "C"

        === "Inheritance"

            [Type punning](https://en.wikipedia.org/wiki/Type_punning) é uma técnica que aproveita do fato que structs podem ser simples e apenas armazenarem os dados em sequência.  

            ```c
            #include <stdio.h>
            #include <stdlib.h>

            struct Base {
                int field1;
            };

            struct Derived {
                struct Base base;
                int field2;
            };

            int main() {
                struct Derived *example = (struct Derived *)malloc(sizeof(struct Derived));

                printf("example->base.field1 = %d\n", example->base.field1);
                printf("example->field2 = %d\n", example->field2);

                struct Base *example2 = (struct Base *)example;

                printf("example2->field1 = %d\n", example2->field1);

                printf("field1 address = %p\n", &(example->base.field1));
                printf("field1 address = %p\n", &(example2->field1));
            }
            ```

            ```
            example->base.field1 = 0
            example->field2 = 0
            example2->field1 = 0
            0x56df3427b2a0
            0x56df3427b2a0
            ```

            Note que precisamos declarar `Base` primeiro para que depois da conversão o tratamento seja correto.  

            Basicamente a memória é organizada como:

            | Address | Base   | Derived |
            | ------  | ------ | ------- |
            | 0x00    | field1 | Base    |
            | 0x04    |        | field2  |

            E já que `Base` é equivalente a `field1`, podemos reescrever como:  

            | Address | Base   | Derived |
            | ------  | ------ | ------- |
            | 0x00    | field1 | field1  |
            | 0x04    |        | field2  |

        === "Encapsulation"

            Utilizando a mesma estratégia de herança, podemos criar um método responsável por criar o objeto (`new_obj`) e apenas disponibilizar ele pelo headers.  

            ```c
            #include <stdio.h>
            #include <stdlib.h>

            struct Base {
                int pub_field;

                void (*pub_method)(struct Base *);
            };

            struct Derived {
                struct Base base;
                int pvt_field;

                void (*pvt_method)(struct Derived *);
            };

            void method1(struct Base *self) {
                struct Derived *s = (struct Derived *)self;

                printf("pub_field = %d\n", self->pub_field);

                s->pvt_method(s);
            }

            void method2(struct Derived *self) {
                printf("pvt_field = %d\n", self->pvt_field);
            }

            struct Base *new_obj() {
                struct Derived *example = (struct Derived *)malloc(sizeof(struct Derived));

                example->base.pub_field = 10;
                example->base.pub_method = &method1;
                example->pvt_field = 20;
                example->pvt_method = &method2;

                return (struct Base *)example;
            }

            int main() {
                struct Base *e = new_obj();

                e->pub_method(e);
            }
            ```

            ```
            pub_field = 10
            pvt_field = 20
            ```

            Isto não impede outras pessoas de incluerem o seu arquivo `.c` e criarem `Derived` manualmente.  
            
            Uma maneira de bloquear este tipo de criação é utilizando anonymous structs com macros para temporariamente ter definição daquela struct.  

            ```c
            #include <stdio.h>
            #include <stdlib.h>

            struct Base {
                int pub_field;

                void (*pub_method)(struct Base *);
            };

            #define DERIVED                                     \
                struct {                                        \
                    struct Base base;                           \
                    int pvt_field;                              \
                    void (*pvt_method)(void *);                 \
                }

            void method1(struct Base *self) {
                DERIVED *s = (DERIVED *)self;

                printf("pub_field = %d\n", self->pub_field);

                s->pvt_method(s);
            }

            void method2(void *self) {
                DERIVED *s = (DERIVED *)self;

                printf("pvt_field = %d\n", s->pvt_field);
            }

            struct Base *new_obj() {
                DERIVED *example = (DERIVED *)malloc(sizeof(DERIVED));

                example->base.pub_field = 10;
                example->base.pub_method = &method1;
                example->pvt_field = 20;
                example->pvt_method = &method2;

                return (struct Base *)example;
            }

            int main() {
                struct Base *e = new_obj();

                e->pub_method(e);
            }

            #undef DERIVED
            ```

            ```
            pub_field = 10
            pvt_field = 20
            ```

            Porém gera uma grande quantidade de warnings devido a falta de segurança quando lidando com anonymous structs.  