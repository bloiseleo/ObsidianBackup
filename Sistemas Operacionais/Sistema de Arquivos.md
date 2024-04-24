Durante a vida do sistema operacional, ele deve ser capaz de armazenar todas informações de maneira persistente e, também, deixar essas informações acessiveis de maneira concorrente. Para fazer isso, existe o sistema de arquivos, que realiza a gerencia de algoritmos que implementam essas funcionalidades.

Os principais conceitos que devem ser aplicados são: 
- Armazenar uma grande quantidade de informações.
- A informação deve sobreviver a finalização do O.S.
- Múltiplos processos devem ser capazes de acessar as informações concorrentemente.

Esse sistema é constituido de duas partes distintas:
- Conjunto de arquivos, que são os dados de fato. Esses arquivos são unidades lógicas de informação criadas por processos.
- Estrutura de Diretórios: Organiza e Fornece informações sobre os arquivos do sistema.
### Arquivos
Cada arquivo é identificado por meio de um nome ( essas regras variam de acordo com o sistema ). Geralmente, temos um identificador alfanumérico e uma extensão, que é separado por ponto. Ademais, essas extensões podem não ser impostas pelo sistema operacional e serem meras convenções.

> No final, um arquivo, nada mais é, que um conjunto de bytes que está armazenado primeiramente em algum lugar do seu armazenamento secundário.

Cada arquivo possui uma organização própria. Essa organização pode ser uma estrutura pelo sistema operacional e/ou definida pela própria aplicação. Nesse caso, existem algumas que são mais utilizadas:
- Sequência Desestruturada de Bytes: Nesse caso, o sistema de arquivos não impõem nenhuma estrutura obrigatória. Dessa forma, a interpretação daqueles bytes é de responsabilidade da aplicação.
- Sequência de Registros de Tamanho Fixo: Nesse caso, o arquivo é armazenado de uma forma estruturada. O arquivo é dividido de acordo uma determinada estrutura e, o acesso a esse arquivo, deve ser realizado lidando com essa estrutura. Um exemplo são os programas armazenados em cartões perfurados. Nesse caso, o arquivo é divido em registros e cada registro possui um tamanho. 
- Árvores de Registros: Nesse caso, o arquivo é composto por registros que não possuem o mesmo tamanho. Cada um contem uma chave em uma posição fixa dentro do registro. A árvore é ordenada pelo campo da chave.
### Métodos de Acesso
Para acessar um arquivo, existem alguns métodos que foram desenvolvidos:

- Acesso Sequencial: O acesso era feito de forma sequencial, ou seja, eram acessados na ordem em que eram gravados. Nesse caso, só era possível criar arquivos no final.
- Acesso Aleatório: O acesso é feito diretamente no começo daquele arquivo. Nesse caso, você pode escrever e/ou ler de qualquer outro pedaço de memória. Além disso, para terem essa tecnologia, é necessário que cada registro tenho um tamanho fixo.
### Tipos de Arquivos

- Regulares: Guarda Informações genéricas, como dados do usuário.
- Diretórios: Arquivos de sistema usados para manter a estrutura do sistema de arquivos.
- Arquivo especial de Caractere: Relacionam-se com operações de E/S e costuma modelar dispositivos reais.
- Arquivos especiais de Bloco: Texto ou Binário.
### Diretórios
Os diretórios servem para organizar os arquivos logicamente. Nesse caso, o diretório é um arquivo que contém uma estrutura de dados com entradas associadas aos arquivos armazenados dentro dele. Cada entrada possui informações sobre esse arquivo.

O sistema mais adotado hoje em dia é o sistema de arquivos em árvore. Nessa estrutura, cada diretório pode conter mais diretórios e, também, arquivos. Por conta disso, cada arquivo possui um caminho que vai desde a raiz até aquele determinado ponto.

## Partições
Um disco diz-se particionado quando um conjunto de bytes é separado e funciona independentemente de outro conjunto de bytes. Na prática, é quase como se tivessemos um HD virtual dentro do físico real. Um HD pode conter uma partição só ou pode ter várias e cada uma pode ter o seu próprio sistema de arquivos.

Cada partição é registrada no disco em uma tabela de partição e, cada partição, deve possuir um sist
### Implementação
A transferência entre memória principal e secundária se dá através de blocos. Cada bloco é constituido por outras divisões lógicas chamadas de setores. O Setor 0 é chamado de  Master Boot Record, que é utilizado durante a inicialização do computador. Ao final desse setor, tem registrado a tabela de partição, que contêm registrado o começo e final de toda partição.

Quando o computador inicia suas operações, a BIOS lê e executa o MBR. Nesse caso, a primeira coisa feita é localizar a partição ativa, ler o seu primeiro bloco (que é o bloco de inicialização) e executá-lo. Esse programa lido no primeiro bloco incializa e carrega o sistema operacional na memória. Mesmo que não haja um sistema operacional, toda partição começa com um bloco de inicialização.

Esse bloco costuma ser um `superbloco`. Esse super bloco contêm informações a respeito do sistema de arquivos e é lido para para a memória quando o computador inicia ou o sistema de arquivos é iniciado. 

Para que possam ser escritos arquivos dentro dessa partição, é necessário saber quais blocos estão livres. Para fazer isso, existem duas implementações: mapa de bits e lista encadeada.
#### Mapa de Bits
No mapa de Bits, temos uma tabela repleta de 0s e 1s onde cada entrada dela corresponde à um bloco. Dessa forma, se for 0, o bloco está livre e, se for 1, o bloco está sendo usado.
#### Lista encadeada
Na lista encadeada, temos cada bloco contendo como informação o endereço para o próximo bloco. Logo, podemos acessar todos os blocos livres a partir do primeiro bloco. Contudo, isso é péssimo, pois precisamos percorrer sequencialmente os blocos e, também, perder espaço para guardar esse endereço.
### Alocações

Na alocação contígua de arquivos, um arquivo é salvo em blocos contíguos de dados no disco. Dessa forma, é armazenado o endereço do primerio bloco do arquivo e quantos blocos ele preenche. Entretanto, essa solução tem um problema: Fragmentação do Disco.

Nesse caso, com o passar do tempo e as alocações sendo realizadas, existe um problema onde você pode acabar tendo muito espaço livre entre diversos blocos ocupados. Dessa forma, todos os espaços juntos poderiam, por exemplo, criar um bloco que suporta mais 2 arquivos. Entretanto, como estão espaçados, eles não suportam nenhum arquivo. 

Nesse caso, acontece a `desfragmentação`, que é custosa e ocorre periodicamente. Ela move os arquivos de bloco para desfragmentar o disco.

Existe, também, a alocação por lista encadeada, onde o arquivo é separado em blocos e cada bloco possui a referência para o próximo bloco. Entretanto, isso torna-se um problema na medida em que os blocos podem ficar alocados em blocos distantes. Dessa forma, há um grande esforço para localizar os pedaços dos arquivos e causa lentidão. 

Além disso, existe o problema onde se um ponteiro for corrompido, perdemos o acesso à todo o arquivo.

#### Alocação por Lista Encadeada com índice 
Nesse caso, os ponteiros de cada bloco do arquivo estão em uma tabela separada e não dentro do arquivo. Embora ainda seja feito acesso sequencial, ela é seguida pela tabela e não no bloco diretamente. Com essa tabela na memória principal, esse processo acelera.

Dessa forma, o diretório só precisa saber o primeiro bloco e ainda consegue ler o arquivo todo. Mas, isso vem com um custo: essa tabela é chamada de File Allocation Table (FAT). Nesse caso, ela pode ficar muito grande se o disco for muito grande.

### Alocação Indexada
Nesse caso, cada arquivo possui uma tabela chamada de `i-node`. Nessa tabela, estão todos os endereços para os outros pedaços de arquivos na memória. Dessa forma, basta acessar o i-node que poderemos acessar o arquivo por inteiro. Além disso, não precisamos alocar continuamente os blocos, uma vez que seus endereços estão armazenados na tabela i-node.

A vantagem que temos nesse método é que: caso o arquivo não esteja aberto, não precisamos mantê-lo na memória.

## Implementação de Cache
O acesso ao disco é mais lento do que o acesso à memória principal. Por conta disso, muitos sistemas operacionais implementam o que é chamado de cache. Nesse caso, o sistema operacional reserva uma área da memória principal para ser utilizada como cache em operações de acesso ao disco.

Logo, antes de acessar o disco, o sistema operacional verifica se já há registros daquele arquivo no cache. Se possuir, ele acessa o cache e recupera os dados. Se não, ele busca na memória secundária e traz pro cache.

O problema é a atualização desse cache. Uma vez que a informação está no cache, é necessário removê-la quando não está sendo mais utilizada.  Para tratar isso, existem duas técnicas:
- Processo que fica de tempos em tempos sincronizando o disco com o cache.
- `write-through`: Essa técnica consiste em sincronizar imediatamente cada bloco que for modificado no cache.
## Evitando Perdas
O disco deve ser atualizado o mais breve possível. Contudo, mesmo com essas medidas, é possível que uma determinada queda de energia ou algum outro acontecimento não permita que as alterações sejam salvas.

Para que isso não ocorra, foi criado o `Journaling`. Nesse caso, existe um local onde as mudanças são previamente escritas de maneira sequencial em vez de serem escritas diretamente no disco. Para isso funcionar, primeiro, o sistema escreve uma transação nesse diário. Uma transação é uma unidade de trabalho que produz um resultado. 

Quando essa transação é escrita no diário, ela é considerada confirmada e o sistema pode seguir adiante. Portanto, depois que são confirmadas, elas são reexecutadas no sistema real. Assim que essa transação é concluida no sistema real, ela é removida do diário.

Logo, quando o sistema desligar e ligar de novo e ainda houver transações naquele diário, elas serão executadas quando o sistema voltar.