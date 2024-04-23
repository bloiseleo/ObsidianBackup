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

No final, um arquivo, nada mais é, que um conjunto de bytes que está armazenado primeiramente em algum lugar do seu armazenamento secundário. 