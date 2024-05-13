A linguagem C foi criada há muitos anos atrás para a elaboração do sistema `Unix`. Entretanto, com o passar dos anos, a American National Standard Institute (ANSI) estabeleceu um manual definindo o padrão de C. Portanto, essa referência é chamada de `ANSI C`. 

O ANSI C define um conjunto de header files, tipos de dados e structs que são fornecidos em tempo de execução. Dessa forma, a biblioteca padrão é bem determinada e, programas que a usam, tem uma garantia de que serão suportados em diferentes arquiteturas.

### Comentários
Os comentários são ignroados pelo compilador e tudo que está dentro desses caracteres `/**/`.
### Funções
Funções são um conjunto de `statements` que realizam alguma computação. Essas funções podem receber um nome, argumentos e definir um tipo de retorno.  Para fazer isso, temos essa sintaxe:

```
retorno_tipo nome_funcao(parametros...)
{
	//corpo da função
}
```

Em C, a função que é chamada quando o processo é iniciado chama-se `main`.  Essa função deve retornar um valor. Geralmente, retorna-se 0 para sucesso e qualquer outro inteiro positivo para erro. Basicamente, qualquer programa em C é um conjunto de funções e variáveis. 

Para invocar uma função, você deve usar o nome dela e passar os argumentos na ordem em que foram declarados. Caso nenhum tenha sido passado, basta informar os parâmetros:

```
nome_funcao(parametros...);
```

Exemplo:

```
int soma(int x, int y) {
	return x + y;
}
```

### Variáveis
As variáveis são espaços de memória 