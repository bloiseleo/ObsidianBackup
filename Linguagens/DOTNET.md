O .NET é uma plataforma de desenvolvimento de aplicações muito similar à JVM do Java. Ele é composto pelos seguintes componentes:
- Runtime: Executa o código de fato.
- Bibliotecas: Fornece a implementação das funcionalidades mais comuns.
- Compilador: Realiza a compilação do código C# e/ou outras plataformas.
- SDK: Ferramentas para auxiliar o desenvolvimento do software.

### Runtime - Common Language Runtime
O Common Language Runtime executa o código produzido pelos compiladores do .NET. Todo código gerado para esse runtime é chamado de `managed code` ou código gerenciado. Nesse caso, o compilador é o responsável por gerar esse código e os metados esperado pelo CLR. Esses metadados são responsáveis por:

- Localizar e carregar classes.
- Layoutar a memória.
- Chamar métodos.
- Gerar código nativo
- Integração cross-language.

#### Processo de Compilação e Execução
O compilador é o responsável por ditar a sintaxe e como você irá escrever o código e acessar os recursos do `Common Language Runtime`. Ele irá compilar o código para Microsoft Intermediate Language, que é independente de CPU. Esse código contem o código intermediário e os metadados para o CLR. 

Para ser executado, esse código precisa ser compilado para código de máquina. Isso é feito pelo compilador JIT do CLR. Como existe um runtime para uma variadade de arquiteturas e sistemas operacionais, você pode fazer código no Linux que roda no Windows - desde que não faça chamadas para bibliotecas específicas de um sistema.

Além disso, nem todo código é automaticamente compilado para CPU-especifico. Nesse caso, somente aquilo que é necessário e chamado durante a execução.

### MSBuild
O Microsoft Build Engine 