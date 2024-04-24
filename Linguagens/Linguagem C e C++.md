Essa linguagem apresenta-se de uma forma onde estão presentes funções e variáveis. Essas funções apresentam `statements` que mandam o computador executar algo. Além disso, as variáveis contém valores que são usados por esses `statements`.
Todo programa em C começa da função `main`. Essa função é a que será executada quando o programa começar a ser executado.
### Variáveis
Todas as variáveis em C devem ser, ao menos, declaradas antes de serem utilizadas. Essas variáveis conterão valores que podem ser usados durante a duração daquele escopo.
### Comentários
Os comentários em C são ignorados pelo compilador e devem começar com `/*` e terminar com `*/`. Todo conteúdo colocado dentro desses caracteres serão ignorados. Além disso, é possível fazer um comentário de uma única linha. Para fazer isso, você deve fazer com o comentário `//`.
### Funções
As funções em C seguem a seguinte sintaxe:
```
retorno nome_Da_funcao(argumentos) {
	// corpo da função
}
```
- O `retorno` deve ser substituido pelo tipo que aquela função retorna
- `nome_Da_funcao` é o nome da função e é esse nome que você usará para chamar essa função em outros arquivos.
- Os `argumentos` são os valores que aquela função espera receber e elas devem ter o seguinte formato: `tipo nome`. O `tipo` é o tipo de valor aceito e, o `nome`, é o nome da variável que deve ser utilizada dentro da função para referenciar-se a esse valor.
- O `// corpo da função` deve estar entre `{}`. Quando isso é feito, um frame é posto na `stack` e dentro dessas chaves você irá especificar os `statements` a serem executados.

Um exemplo é a própria função `main` com o hello world:

```
#include <stdio.h>

int main() {
    printf("hello, world\n");
    return 0;
}
```

### Pré-Processamento
O pré-processamento ocorre antes de realizar a compilação de um arquivo C. Geralmente, temos diretivas que serão processados por essa etapa e cada uma produz um resultado diferente. Nesse caso, vale a pena ver uma por uma.

Uma das que mais usamos é o `#include`. Nesse caso, o `#include` será substituido pelo conteúdo integral do arquivo que está sendo incluido. O import é diferente de acordo com o tipo de import. Se for por `< e >`, ele será buscado em uma lista pré-definida pelas configurações do compilador. Se for `" e "`, ele será buscado no diretório local e em uma lista padrão pré-definida.
### Header Files
Os arquivos header são arquivos onde podemos determinar e declarar entidades que serão usadas pelo nosso código. Esses arquivos, por sua vez, podem ser injetados em outros arquivos que são necessários. Ao fazer isso, usamos a diretiva de pré-processamento chamada de `include`. Dessa forma, durante a compilação, temos as assinaturas e declarações prontas dentro do arquivo. Contudo, ainda precisamos da definição das funções. Essas definições estão dentro do arquivo de mesmo nome, porém terminado em `.c`.

Por exemplo, podemos ter um arquivo chamado de `.h`:

```
#ifndef LIST_H
#define LIST_H
#define BUFF_START 10
struct list;
typedef struct list List;
List* new_List();
int getItem_List(List* self, int index);
int setItem_List(List* self, int index, int value);
int shiftItem_List(List* self, int value);
int popItem_List(List* self);
char* List_toString(List* self);
#endif
```

> Acima, vemos um `#ifndef LIST_H`. Esse cara é um header guard. Ele impede que esse código seja colado mais de uma vez, caso ele já esteja presente.

Dessa forma, definimos uma struct, uma constante e as funções. Logo, teremos outro arquivo contendo as suas definições de fato:

```
#include <stdlib.h>
#include "list.h"

struct list {
    int length;
    int* arr;
};

List* new_List() {
    List* l = (List*) malloc(sizeof(List));
    l->length = 0;
    l->arr = (int*) malloc(sizeof(int) * BUFF_START);
    return l;
}

char* List_toString(List* self) {
    if(self->length == 0) {
        return "[]";
    }
}
```

Pronto, dessa forma, podemos importar o arquivo da seguinte forma:

```
main.c
-----------------------------------------------------------------------------------
#include <stdio.h>
#include "list.h"
int main() {
    List* list = new_List();
    printf("%s\n", List_toString(list));
    return 0;
}
```

Perceba a diferença entre o import de um arquivo header presente no sistema e um presente no path local. A diferença está no que está englobando o nome desse header file: `<` para arquivos do sistema `>` e `"` para arquivos do usuário `"`.

Ademais, é importante salientar que é importante realizar a compilação de um arquivo que não é executável sem realizar a linkagem. Para fazer isso, devemos passar o parâmetro `-c` para o `gcc`, por exemplo.
