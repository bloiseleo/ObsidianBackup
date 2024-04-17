  O java é uma linguagem de programação estaticamente tipada e completamente orientada a objetos. Além disso, essa linguagem é executada dentro da `Java Virtual Machine`, que é uma camada entre o sistema operacional e o código que será executado. Nesse caso, o processo de execução da linguagem se dá da seguinte forma:

```
Código Fonte -> Javac (Compilação) -> Bytecode -> (Interpretação) JRE (JVM).
```

Para desenvolver em Java, precisamos do JDK. O Java Development Kit é um conjunto de ferramentas que nos possibilitam desenvolver programas em Java. Ele consiste em diversas bibliotecas para desenvolvimento e a própria JRE. Essa, por sua vez, é a única coisa necessária que o cliente terá que ter instalado na máquina ou servidor para executar esse software.
### Execução
Quando instalamos o JDK, recebemos um binário chamado `java`e outro binário chamdo `javac`. Esses dois binários trabalham juntos. O binário `java` serve para invocar a JVM passando como parâmetro um arquivo `.class` contendo uma classe que é executável. Para ser executável, ela deve conter um método `main` estático e público e, a classe, deve ser pública. Durante o processo de execução, essa classe pode requisitar outras classes. Para realizar o processo de busca dessas classes, a JVM busca em todas as localizações dentro do `classpath`. Por padrão, esse `classpath` é `.`. Logo, nesse caso, ele verifca somente no diretório atual. Para alterar, você pode alterar passando um parâmetro: `-cp`.
