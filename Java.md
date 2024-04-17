  O java é uma linguagem de programação estaticamente tipada e completamente orientada a objetos. Além disso, essa linguagem é executada dentro da `Java Virtual Machine`, que é uma camada entre o sistema operacional e o código que será executado. Nesse caso, o processo de execução da linguagem se dá da seguinte forma:

```
Código Fonte -> Javac (Compilação) -> Bytecode -> (Interpretação) JRE (JVM).
```

Para desenvolver em Java, precisamos do JDK. O Java Development Kit é um conjunto de ferramentas que nos possibilitam desenvolver programas em Java. Ele consiste em diversas bibliotecas para desenvolvimento e a própria JRE. Essa, por sua vez, é a única coisa necessária que o cliente terá que ter instalado na máquina ou servidor para executar esse software.
### Execução

Quando instalamos o JDK, recebemos um binário chamado `java`e outro binário chamdo `javac`. Esses dois binários trabalham juntos. O binário `java` serve para invocar a JVM passando como parâmetro um arquivo `.class` contendo uma classe que é executável. Para ser executável, ela deve conter um método `main` estático e público e, a classe, deve ser pública. Durante o processo de execução, essa classe pode requisitar outras classes. Para realizar o processo de busca dessas classes, a JVM busca em todas as localizações dentro do `classpath`. Por padrão, esse `classpath` é `.`. Logo, nesse caso, ele verifca somente no diretório atual. Para alterar, você pode alterar passando um parâmetro: `-cp`.
### Convenções

Todo arquivo em java deve ter uma classe cujo nome é o mesmo do arquivo. O nome da classe deve ter a primeira letra maiúscula.
- Você pode ter outras classes dentro do mesmo arquivo, mas uma precisa obrigatoriamente seguir acima.
- O nome das variáveis é camelCase.
- Constantes são maiúsculas.

### Variáveis
As variáveis são locais onde iremos guardar valores e/ou referências a objetos. Como o Java é fortemente tipado, precisamos especificar o tipo da variável e/ou de uma forma que o java consiga inferir o tipo daquela variável:
```
tipo nome_da_variavel; // Declaração
tipo nome_da_variavel = valor; // Inicialização
```
Os tipos das variáveis determinam o que ela pode fazer e para que ela pode ser utilizada. Cada uma possui suas propriedades e são melhor utilizadas para determinar certos dados.

Existem os seguintes tipos em Java:

- int: Representa um número inteiro na base 10 e ocupa 4 bytes.
- byte: Representa um número inteiro na base 10 e  ocupa 1 byte de memória.
- short: Representa um número inteiro na base 10 e ocupa 2 byte de memória.
- long: Representa um número inteiro na base 10 e ocupa 8 bytes de memória.
- float: Representa um número decimal na base 10 e ocupa 4 bytes de memória.
- double: Representa um número decimal na base 10 e ocupa 8 bytes de memória.
- boolean: Representa um valor verdadeiro ou falso e costuma ocupar 1 bit.
- char: Representa um caracter e esse caracter geralmente é baseado na tabela ASCII.

Esses tipos não são considerados objetos e são armazenados diretamente na stack. 

Para determinar constantes, utilizamos a palavra chave `final`. Esse palavra chave