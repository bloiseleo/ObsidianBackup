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
- Arquivo especial de Caractere: