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
O Microsoft Build Engine é uma build tool para gerenciar e compilar projetos. Essa ferramenta é configurada por um arquivo XML que controla e determina todo o processo de build.

## Sintaxe e Estrutura do Projeto
Quando inciamos um projeto C#, temos um arquivo chamado `Program.cs`, que geralmente é o ponto de entrada da aplicação, um arquivo terminado em `.csproj` com o nome do Projeto, que é o arquivo do `MSBuild` utilizado para buildar a aplicação com algumas configurações que dependem de cada projeto, uma pasta bin e uma pasta obj. A pasta bin contêm os binários da aplicação, que é gerado quando você compila a aplicação, e, também, dentro da pasta obj. Nesse caso, dentro da pasta obj, teremos arquivos de debbuging.

> Tanto a pasta bin como a pasta obj devem ser ignoradas quando versionamos nosso projeto.

Qualquer projeto C# tem que ter um método `Main` que seja acessível pela CLR para ser chamado na inicialização do programa. Caso exista mais de um, você precisa dizer no momento da compilação qual a classe que será usada como ponto de entrada. Além disso, o método `Main` deve estar dentro de uma classe ou `struct` e deve ser `static`.
### Namespaces
Os namespaces são uma forma que o C# usa para organizar as classes dentro de um determinado projeto e, também, das classes do C#. Todas as classes do C# estão contidas dentro de um `namespace`. Ao fazer isso, o nome da classe deixa de ser somente aquele declarado pelo programador e passa a ser `NomeDoNameSpace.NomeDaClasse`. Esse mecanismo é idêntico ao full qualified name do java.

Por conta disso, podemos ter duas classes num projeto com o mesmo nome, porém em diferente namespaces. Para declarar um namespace, você precisa fazer essa declaração no começo do arquivo da seguinte forma:

```
namespace NomeDoNamespace 
{
	//... declaração de classes
} // Outra forma abaixo:

namespace NomeDoNamespace;
// declaração de classes
```

Toda a declaração dentro de namespaces passa a pertencer a ele.

Para usar essa classe ou recurso, você precisa usar o nome completo daquela classe ou recurso levando em conta o `namespace` declarado da seguinte forma:
```
public class Program {
	public static void Main(string[] args) {
		var obj = new NomeDoNamespace.Classe();
	}
}
```

Entretanto, para encurtar esse caminho, você precisa utilizar a declaração `using`. Essa declaração permite você usar um `namespace` de modo em que você use somente o nome da classe:

```
using NomeDoNamespace;
public class Program {
	public static void Main(string[] args) {
		var obj = new Classe();
	}
}
```
### Classes 
A declaração de classes no C# é feita com a palavra reservada `class`.  Essa palavra é seguida pelo nome da classe, que deve ser maiúsculo e ser igual ao nome do arquivo. Antes dela, podemos ter um modificador de acesso:

```
class Program {
    public static void Main(string[] args) {

    }
}
```

O exemplo acima motra a primeira classe sendo chamado como entrypoint do C#.

> A convenção do C# é que métodos e propriedades públicas devem começar com maiúsculos e seguir minúsculo enquanto que, privados ou protegidos, devem ser camelCase.