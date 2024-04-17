A arquitetura de computadores é a área da computação que é reponsável por projetar e determinar os componentes funcionais de um computador para que o mesmo seja capaz de realizar um conjunto de tarefas e cumpra determinadas funções. Um desses aspectos é o `Instruction Set`. O Instruction Set determina os tipos, dados, registradores, como a manipulação da memória será realizada e etc. Nesse caso, podemos entender que uma CPU é uma implementação desse Instruction Set.

> Dessa forma, os binários que rodam em uma CPU podem rodar em qualquer outra CPU, desde que sejam do mesmo Instruction Set. 

Tudo dentro do computador é 0 e 1. Logo, podemos entender que o bit é a unidade de informação mais básica do computador. Geralmente, para facilitar a leitura, sempre agrupamos os bits em algum grupo com base em determinadas regras:

- Byte: Grupo de 8 bits.
- KiloByte: 2^10 bytes (1024 bytes).
- MegaByte: 2^20  bytes.
- GigaByte: 2^30 bytes.
- TeraByte: 2^40 bytes.
- PetaByte: 2^50 bytes.

Para subir nessa escala, você divide o valor pelo alvo. Por exemplo, de byte para TeraByte podemos dividir por 2^40. Entretanto, para descer, fazemos a operação inversa: multiplicamos pela distância. Logo, nesse exemplo, multiplicariamos por 2^40.

O valor dos bits diminuiu e aumenta da mesma forma que o valor em base 10: da direita para esquerda. Entretanto, geralmente, é referido como o bit menos significante (mais a direita) e mais significante (mais a esquerda).

Caso alguma operação sobre os bits gere um resultado que não pode ser armazenado por falta de espaço, ocorre um overflow. Esse overflow terá que ser lidado de alguma forma e isso depende da linguagem de programação, o sistema operacional e o programa.

### Complemento de 2
Para representar números negativos, o hardware optou por tornar o dígito mais significativo como um indicador de sinal. Nesse caso, se for 0, ele é positivo e, se for 1, é negativo. 

Os números positivos são representados de maneira direta, ou seja, ele possui o 0 no `MSB`e para calcular o seu valor basta aplicarmos as operações de conversões que sabemos.

Entretanto, quando falamos de números negativos, ele tem o 1 no `MSB`e, para calcular o seu valor, deve-se inverter todos os bits (o que é 0 vira 1 e o que é 1 vira 0) e somar de 1. No final, teremos o número positivo equivalente e podemos realizar a conversão normal.

Para converter de positivo para negativo, iremos realizar a inversão de todos os bits e, em seguida, somar de 1. Nesse caso, teremos o resultado do número negativo.
### Instruções

Ainda dentro desse computador, ele precisa receber instruções. Essas instruções nada mais são que um conjunto de dados binários que representam uma ação. Entretanto, escrevê-las na mão em formato binário é muito chato e difícil. Então, inventaram um `assembler`. Esse assembler transforma uma instrução escrita de uma forma em formato binário. Por exemplo: `add A,B`, depois de passar pelo assembler, `1000110010100000`. Entende agora por quê é mais fácil escrever assembly?

O nome para essa linguagem é o `Assembly`e nos permite escrever código quase que nativo para o CPU.  Entretanto, ele tem poucas abstrações e possui mais proximidade com o computador.

Para entender mais sobre Instruction Set, veja [Instruction Set](obsidian://open?vault=Vault&file=Arquitetura%20de%20Computadores%2FInstruction%20Set)
## Componentes
Os principais componentes de um computador ficam em 5 categorias:

- Input: Recebe dados e os envia para dentro do computador.
- Output: Recebe dados do computador que advem de algum processamento interno.
- Memoria: Armazena dados.
- Datapath: Realiza as operações aritméticas.
- Controle: Controla os outros componentes.

Todos os componentes ficam em uma dessas 5 categorias.