O java é uma linguagem de programação estaticamente tipada e completamente orientada a objetos. Além disso, essa linguagem é executada dentro da `Java Virtual Machine`, que é uma camada entre o sistema operacional e o código que será executado. Nesse caso, o processo de execução da linguagem se dá da seguinte forma:

```
Código Fonte -> Javac (Compilação) -> Bytecode -> (Interpretação) JRE (JVM).
```

Para desenvolver em Java, precisamos do JDK. O Java Development Kit é um conjunto de ferramentas que nos possibilitam desenvolver programas em Java. Ele consiste em diversas bibliotecas para desenvolvimento e a própria JRE. Essa, por sua vez, é a única coisa necessária que o cliente terá que ter instalado na máquina ou servidor para executar esse software.

Quando instalamos o JDK, recebemos: um binário chamado `java`e outro binário chamdo `javac`. Esses dois binários trabalham juntos. O `java` serve para invocar a JVM passando como parâmetro um arquivo `.class` contendo o código que será executado. O `javac`, por sua vez, será usado para compilar os arquivos.