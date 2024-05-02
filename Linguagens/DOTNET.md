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

### Tipos de Dados
Existem os seguintes tipos de dados:
- string: Conjunto de caracteres encodados com o UTF-8.
- char: Caracter unicode.
- int: Número inteiro com sinal de 32 bits de tamanho.
- float: Número decimal com sinal e 32 bits de tamanho com precisão de uma casa decimal.
- decimal: Números decimais com sinal de 28 a 29 dígitos significativos.
- double: Números decimais com sinal com 64 bits de tamanho e precisão de duas casas decimais.
- long: Número inteiro com sinal de 64 bits de tamanho.
- unit: Número inteiro sem sinal de 32 bits de tamanho.
- short: Número inteiro com sinal de 16 bits de tamanho.
- ulong: Número inteiro sem sinal de 64 bits de tamanho.
- object: Tipo base de todos os objetos.
- byte: Inteiro sem sinal de 8 bits.

> Para criar um `decimal`, você precisa fazer da seguinte forma: decimal preco = 1.80M; É necessário adicionar o sufixo M depois do valor.

Ainda temos mais um tipo, o tipo `DateTime` no C# é usado para representar uma Data com horário, data e o timezone.

Por fim, todos os tipos herdam de `Object`, que é uma classe base de todas as derivações. Essa classe é extendida automaticamente e sem nós sabermos. P
### Operações em Tipos

Os operadores aritméticos possuem os valores de precedência que sobre eles existem. Nesse caso, estamos falando do `+, -, / e *`. A prescedência pode ser aplicada sobre eles de acordo com a ordem natural `* e / - + e -` nessa ordem respectivamente.
#### Concatenação de Strings
Para concatenar as strings, podemos utilizar o operador `+` e/ou fazer uma `template string`:
```
int num = 1;
Console.WriteLine("Número: " + num);
Console.WriteLine($"Número: {num}");
```

### Datas
Em C#, as datas são representadas pela classe `DateTime`.  Além disso, essa classe carrega consigo, também, o fuso horário da data. Por padrão, ele leva em consideração o fuso horário da data.
A formatação da data pode ser feita de maneira direta, ou seja, pode ser feita dessa forma:
```
Console.WriteLine(data);
```
Essa formatação leva em consideração o `CultureInfo` para formatar a data. Essa informação é procurada no sistema operacional. Para formatar de outra forma, temos um método chamdo `ToString()`, que aceita uma formatação:
```
Console.WriteLine(now.ToString("dd/MM/yyyy"));
```
Vale a pena dar uma olhada na documentação para entender quais formatações estão funcionando.  Para pegar somente a data sem a hora, podemos usar o método `ToShortDateString()`. Para pegar somente a hora, use o método `ToShortTimeString()`.

Para converter de `string`  para `DateTime`, podemos utilizar o `Parse`, `TryParseExact` e `TryParse`. O `Parse` irá lançar uma exceção caso não consiga converter e, o `TryParseExact` e `TryParse`, irá converter e retornar `true ou false` para o sucesso ou falha. A diferença entre o `TryParse` e `TryParseExact` é justmanete na precisão oferecida. No `TryParse`, você não precisa informar nada além da data. Enquanto que, no `TryParseExact`, você precisa fornecer o formato que a data está, cultura, estilo e aonde será armazenado.
### Formatação
A formatação é um tratamento dos dados antes desse dado ser exibido. Existem diversas formas de formatar:
- Dinheiro: Podemos formatar valores ao interpolar strings da seguinte forma `${value:C}`. Essa formatação pega a localização do sistema e utiliza para formatar corretamente.
- ToString: O método `ToString` implementado por padrão nos permite formatar como um determinado valor será representado. Nesse caso, para fazermos a mesma coisa do de cima, fazemos da seguinte forma: `Console.WriteLine(value.ToString("C", CultureInfo.CreateSpecificCulture("pt-BR")))`
- C1, C2, C3, ...: Nessa formatação, não especificamos a cultura, mas especificamos a quantidade de casas decimais representadas.
- P: Nessa formatação, representamos um valor entre 0 e 1 como porcentagem. Por exemplo: `Console.WriteLine(value.ToString("P")) -> %50.00`.
- `#`: Nessa formatação, estamos trabalhando com números, onde podemos definir onde irá entrar dígitos com a cerquilha e onde não irá entrar com qualquer outro caracter ou espaço.

### Localização e Internacionalização
Por padrão, o C# irá recuperar essa informação do sistema operacional que a máquina que está rodando apresenta.  Para alterá-la em tempo de execução, precisamos alterá-la no código. Para fazer isso, usamos uma classe chamada `CultureInfo`. Essa classe apresenta informações referentes ao sistema de escrita, calendário, moeda e outras informações necessárias para localização. Para alterar, podemos usar a seguinte sintaxe:

```
CultureInfo.DefaultThreadCurrentCulture = new CultureInfo("");
```
Como parâmetro, passamos a localização. Para o Brasil, podemos passar `pt-BR` e, para inglês, `en-US`.
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

### Exceções 
Uma exceção é um erro que ocorre dentro de uma rotina. Geralmente, ela ocorre devido à um problema que é irremediável durante a execução ou um problema que impede a execução daquele fluxo.
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

### Indexadores
Os indexadores nos permitem fazer uma sintaxe de `arrays`em qualquer classe que quisermos. Para fazer isso, usamos esses caras: os indexadores. Eles são feitos a partir de um método dentro de uma classe que você declarada dessa forma:
```
public T this[int i]

{
	get {return arr[i];}
	set {arr[i] = value;}
}
```

Dessa forma, estamos permitindo o acesso via índice aos nossos objetos enquanto mantemos controle total sobre quem está sendo acessado e como. Nesse caso, estamos aceitando um inteiro como parâmetro, pois o usuário deve passar um inteiro para acessar 0-indexed. Por fim, você pode ter mais de um desse na classe, ou seja, podem sofrer overload.