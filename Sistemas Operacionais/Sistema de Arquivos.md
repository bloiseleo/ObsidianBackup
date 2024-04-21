Durante a vida do sistema operacional, ele deve ser capaz de armazenar todas informações de maneira persistente e, também, ser acessível de maneira concorrente. Para fazer isso, existe o sistema de arquivos, que realiza a gerencia de algoritmos que implementam essas funcionalidades.

Esse sistema é constituido de duas partes distintas:
- Conjunto de arquivos, que são os dados de fato. Esses arquivos são unidades lógicas de informação criadas por processos.
- Estrutura de Diretórios: Organiza e Fornece informações sobre os arquivos do sistema.
### Arquivos
Cada arquivo é identificado por meio de um nome ( essas regras variam de acordo com o sistema ). Geralmente, temos um identificador alfanumérico e uma extensão, que é separado por ponto. Ademais, essas extensões podem não ser impostas pelo sistema operacional e serem meras convenções.

No final, um arquivo, nada mais é, que um conjunto de bytes que está armazenado primeiramente em algum lugar do seu armazenamento secundário. 