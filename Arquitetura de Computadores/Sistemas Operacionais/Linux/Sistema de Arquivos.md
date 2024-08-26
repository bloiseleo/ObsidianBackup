No caso do Linux, um arquivo é qualquer coisa que possa manipular dados. Nesse caso, cada objeto tem as suas especificidades escondidas atrás de um `Virtual File System - VFS`. Nesse caso, temos alguns tipos de arquivos que são reconhecidos pelo VFS:
- I-NODE: arquivo individual.
- ARQUIVO: Arquivo aberto.
- Superbloco: Um sistema de arquivos inteiro.
- Dentry: Representa uma entrada de diretório individual.

Para cada um desses tipos, o VFS implementam um conjunto de chamadas de sistemas e cada objeto possui um ponteiro para uma tabela de funções que apontam para as chamadas reais.

### Objetos Arquivos
Esses objetos representam arquivos abertos e cada processo que solicita essa abertura receberá um objeto desse tipo.

### Objetos I-Nodes
Esses objetos são os arquivos de fato. Logo, só existe um deles. Os processos podem solicitar a abertura desses i-nodes e, por sua vez, recebem `arquivos`.

### Objetos Superblocos 
Os superblocos dão acesso a i-nodes. Nesse caso, existe um para cada dispositivo de disco montado e sistema de arquivos de rede.

### Objetos Dentry
Representam um diretório de arquivos.

A primeira versão do linux implementava o MINIX, que era bem limitado. Com o passar do tempo, veio o `ext`, que melhorava o `MINIX`, mas ainda era menos performático. Por fim, veio o `ext2`, que passou a ser o principal do linux.

> O linux não atribui significado nenhum para a extensão de arquivos.

### Diretórios do Linux.

`/` -> Raiz;
`/bin` ->  Arquivos executáveis;
`/boot` -> Arquivos de configuração necessários para incialização do sistema.
`/dev` -> Contêm os dispositivos do sistema.
`/etc` -> Arquivos de configuração, scripts de inicialização e etc.
`/home` -> Arquivos dos usuários.
`/lib` -> Bibliotecas e módulos do sistema.
`/lib64` -> Mesma coisa do lib, mas tem coisas para arquitetura 64 bits.
`/media` -> Onde são montados dispositivos externos.
`/mnt` -> Local para montagem manual de dispositivos.
`/opt` -> Fornece um local opcional para aplicações a serem instaladas. 
`/proc` -> Diretório para manter informações a respeito do sistema.
`/root` -> Diretório home do root.
`/srv` -> Arquivos de serviço do sistema.
`/tmp` -> Contém arquivos temporários.
`/usr` -> Aplicativos e arquivos que são, na maioria das vezes, acessíveis para todos os usuários.
`/var` -> Arquivos de logs e bancos de dados.

### EXT2

Numa partição com ext2, temos o seguinte layout:
- Incialização (MBR).
- Superbloco
- Descritor do grupo: localização do mapa de bits, quantidade de blocos livres e i-nodes no grupo. Dois mapas de bits ( um para os blocos livres e i-nodes livres) e cada mapa contêm um bloco de comprimento.
- I-nodes onde cada i-node tem 128 bytes de comprimento e descreve um arquivo.
- Blocos de dados: arquivos e diretórios reais.

Os diretórios ficam mais dispersos e, os arquivos, procuram ser colocados no mesmo grupo de blocos do disco que o i-node.

