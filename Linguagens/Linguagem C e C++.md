A linguagem C foi criada há muitos anos atrás para a elaboração do sistema `Unix`. Entretanto, com o passar dos anos, a American National Standard Institute (ANSI) estabeleceu um manual definindo o padrão de C. Portanto, essa referência é chamada de `ANSI C`. 

O ANSI C define um conjunto de header files, tipos de dados e structs que são fornecidos em tempo de execução. Dessa forma, a biblioteca padrão é bem determinada e, programas que a usam, tem uma garantia de que serão suportados em diferentes arquiteturas.

### Hello World

```
#include <stdio.h>

int main() {
	printf("Hello World!");
	return 0;
}
```

Em C, a função que é chamada quando o processo é iniciado chama-se `main`.  Essa função deve retornar um valor. Geralmente, retorna-se 0 para sucesso e qualquer outro inteiro positivo para erro. Basicamente, qualquer programa em C é um conjunto de funções e variáveis. Funções é um conjunto de `statements` que realizam alguma computação e, variáveis, são espaços de memória que armazenam valores temporariamente.