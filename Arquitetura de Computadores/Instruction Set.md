Um *Instruction Set* é uma camada de abstração entre o hardware e software de menor nível. Essa camada contêm toda a informação para escrever um código que irá ser executado corretamente. Além disso, esse instruction set pode ser combinado com o Sistema Operacional. O sistema operacional encapsula as partes mais baixo nível para que programadores de aplicação não se preocupem com isso. Portanto, o sistema operacional + o instruction set é chamado de `application binary interface (ABI)`.

Dessa forma, as instruções e funções de um computador podem ser debatidos sem debater a implementação em hardware.

## Dentro do Instruction Set
O instruction set contêm instruções que um computador é capaz de executar. Essas instruções são escritas em `Assembly`e, também, em binário. O instructio set irá ser diferente para cada arquitetura. Por exemplo, para processadores intel, geralmente, temos o IS x86 e, em processadores ARM, temos a arquitetura ARM.

Um exemplo de instrução pode ser a de realizar a soma, que podemos ver da seguinte forma:

```
	add c, a, b
```

Nessa instrução acima, temos o seguinte:
- Instrução `add`: Some dois números e armazene o resultado.
- Destino `c`: Guarde o resultado em `c`.
- Operandos: `a`, `b`.

### Registradores
Os registradores são espaços dentro da CPU que armazenam valores temporariamente para realizar alguma determinada função. Esses registradores apresentam um tamanho bem pequeno e aparecem em grupos menores. Contudo, eles são extremamente rápidos.

No instruction set do MIPS, cada registrador possui 32 bits de largura e possui 32 registradores. Dessa forma, somente esse número de registradores pode ser utilizado durante toda a operação desse hardware.

O ponto acima poderia tornar-se um problema quando falamos de estrutura de dados bem grandes. Entretanto, isso pode ser resolvido com a memória principal. 

### Da Memória para Os Registradores
Quando falamos de estruturas de dados que não cabem dentro de um registrador, esses dados são guardados na memória principal. Logo, quando vamos trabalhar com elas, precisamos pegar os dados em si que vamos trabalhar e trazer para o registrador.

Imagine um array para o exemplo abaixo:

Para carregar dados da memória, existe uma instrução chamada de `load`. Essa instrução é responsável por carregar um dado da memória para o registrador. Para fazer isso, o comando espera que você digite da seguinte forma:

```
load registrador_, int_constant(registrador_)
```

O primeiro registrador que aparece no comando é o registrador que irá receber o valor que vem da memória. Em seguida, informamos uma constante e, dentro de `()`informamos o registrador que contêm o endereço base do array na memória. Dessa forma,  esse endereço base é somado com a constante e resulta no endereço que será acessado.

> Esse ponto acima mostra como arrays são resolvidos e tratados em linguagens como C e C++ onde temos a seguinte sintaxe: ```
   int[10] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

Quando acessamos o elemento nesse array, ele faz exatamente esse cálculo.

### Valores Constantes
Grande parte das instruções que vimos até agora precisa que dois dados estejam em um registrador para ser utilizado. Nesse caso, precisariamos antes de operar carregar o valor no registrador e, após isso, pegar esse valor e realizar a a operação. Para evitar esse trabalho, precisamos de instruções que aceitem esse valor constante (e eles existem). Uma das versões da instrução `add` que suporte constante, temos a `addi`. Esse `addi`significa `Add Immediate`.

```
addi $s3, $s3, 4
```

### Formato de Instrução
Cada instrução apresenta um formato que será entendido pelo computador. Cada arquitetura tem o seu próprio formato. Por exemplo, as instruções do MIPS possuem 32 bits. Ademais, cada instrução está presente dentro de um `field`. Esses fields possuem tamanhos específicos e podem receber um nome para expressar a ideia da instrução que ele irá receber:

- O mais padrão de todos é o `opcode`. Esse `opcode` está presente em várias instruções e denota o comando que está sendo executado.