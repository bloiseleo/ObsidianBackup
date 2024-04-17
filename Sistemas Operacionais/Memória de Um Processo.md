### Políticas de Alocação 
As políticas de alocação descorrem sobre como a alocação de memória para determinado processo pode ocorrer. Antigamente, não era necessário esse tipo de coisa, visto que os sistemas eram monoprogramáveis e, por isso, a memória era dividida entre o sistema operacional e o processo rodando. 

Com os sistemas multiprogramáveis, surgiu a necessidade de manter mais programas em execução. Dessa forma, vários programas passaram a ocupar a memória RAM. Portanto, surgiu essa necessidade de gerenciar melhor a memória alocada para cada processo no decorrer de vida do mesmo.
#### Alocação Contígua
A alocação contígua é a política onde o processo, ao ser iniciado, requesita toda memória necessária de uma vez só e, esse bloco de memória, fica alocado durante toda a vida do processo. Entretanto, isso gera um problema: nem toda essa memória é, de fato, usada instantâneamente durante o processo. Portanto, isso desperdíca memória e, também, pode tornar indisponível algum programa, pois não pode ser carregado totalmente.
#### Overlay
Nessa técnica, faz-se necessário dividir o programa em módulos diferentes tornando um módulo como principal e os outros módulos como módulos secundários, terciários e etc. Nesse processo, os módulos devem ser independentes entre sí. 

O primeiro passo é carregar o módulo principal em memória, que irá prevalecer durante toda a execução. Depois disso, conforme a execução, os módulos são requisitados conforme a necessidade e alocam espaço na memória. Depois que eles não são mais necessários, a memória para esse módulo é liberada.

Nesse caso, há a necessidade de que cada módulo seja independente para que possam ser chamados em momentos diferentes e, assim, recebam a mesma locação de memória.


> Essas duas técnicas são aplicadas durante os sistemas operacionais monotarefa. Agora, abaixo, teremos as técnicas mais específicas para sistemas multiprogramáveis.

#### Alocação Particionada Fixa
Nesse caso, a memória destinada aos processos do usuário seria particionada em diferentes tamanhos. Conforme os processos forem requisitando memória, o processo é encaixado na partição que cabe àquele processo. Essas partições são fixas e não mudam durante a execução.

Para suportar mais processos do que o número de partições, é feito filas. Essas filas podem ser organizados de duas formas:
- Fila de Entrada por Partição: Nesse tipo de fila, cada processo fica numa fila esperando a sua partição ficar livre.
- Fila de Entrada Geral: Nesse tipo de fila, todos os processos ficam na mesma fila esperando uma partição que o caiba ficar livre para ser executado.

Esse tipo de alocação gera um problema referente ao desperdício de memória. Quando um processo não ocupa toda a memória, essa memória fica ociosa e não pode ser utilizada. Portanto, foi pensado uma melhor maneira.

#### Alocação Particionada Variável
Nesse tipo de alocação, toda memória não utilizada é classificada como uma partição livre por si só. Quando uma memória é solicitada pelo processo que irá iniciar, uma partição com o tamanho desse processo exato é criado. Todos os outros processos realizam o mesmo procedimento.

Quando um processo requesita mais memória e não tem mais espaço, esse processo aguarda a liberação de um espaço de memória contígua que caiba esse processo.  Depois que um espaço é liberado, esse processo é alocado. 

Para realizar esse tipo de alocação, existem algumas políticas:
- Best-Fit: Todas as partes livres são percorridas em ordem de achar a partição que gerará o menor fragmento de memória livre. O problema acontece devido a necessidade de percorrer todos os espaços livres.
- First-Fit: Nesse caso, o processo é alocado na primeira parte livre em que ele couber. Ele irá agrupar os processos menores separadamente dos maiores e é mais rápido, visto que ele irá percorrer somente até o ponto onde a memória é suficiente.
- Worst-Fit: Nese caso, o processo é alocado na maior partição disponível que ele couber. Nesse caso, sempre caberá um processo pequeno no fragmento resultante. Entretanto, sofre do mesmo problema que o `Best-Fit`.
#### Fragmentação
Um problema que surge dessa solução é que, ao longo do tempo, espaços menores podem ser deixados entre processos e dentro deles. Quando um espaço muito pequeno seria deixado para fora daquele processo, muitas vezes, ele é incorporado ao processo, pois o esforço para manejá-lo não compensa. Dessa forma, temos uma fragmentação `interna`. Quando o espaço pequeno é deixado entre processos, esse tipo de fragmentação é `externa`.

- Uma possível solução seria mover todo esse espaço livre para um espaço contíguo de memória. Contudo, o custo de processamento não compensa na liberação de memória. 
- Outra possível solução seria permitir a alocação de memória não contígua.

### Swap
O swap é uma técnica que visa liberar memória quando um determinado processo não está sendo utilizado. Nesse caso, quando o processo está bloqueado ou em espera, ele será movido para a memória secundária. Portanto, um espaço maior de memória contígua fica liberado e outro processo pode ser alocado. Quando esse processo vai sair do estado bloqueado e/ou em espera, ele é realocado na memória.

Entretanto, esse processo de swap custa bastante tempo de processamento, pois a memória secundária consome bastante tempo para transferir bytes quando em comparação com a memória principal.

> Como esse processo custa muito tempo,  sistemas operacionais modernos implementam outra forma de gerenciamento de espaço livre.

### Memória Virtual

Todo endereço de memória virtual deve ser mapeado para um endereço físico real na máquina. Isso é feito, em grande parte, pelo Sistema Operacional.  Logo, esse conjunto de endereços virtuais pode ser muito maior que o conjunto de endereços físicos.

- Conjunto de endereços físicos: Espaço de Endereçamento Físico.
- Conjunto de endereços virtuais: Espaço de Endereçamento Virtual.

Dessa forma, quando o processo é carregado na memória, ele fica somente com uma parte (que está sendo executada) na memória principal e, o resto, fica no disco rígido. Quando outras partes necessárias, essas partes são carregados pelo sistema operacional. Por conta disso, a memória agora não é mais contígua.

A memória, nos dias de hoje, é dividida em blocos de memória reais e virtuais. Para cada processo, é mantido uma tabela que determina quais blocos da memória virtual do processo estão para os blocos reais da máquina.

### Paginação da Memória
Os endereços de memória são agrupados em um conjunto de endereços chamados de página. Nesse caso, a memória principal acompanha essa divisão e tem diversos quadros de mesmo tamanho. Todas as páginas tem o mesmo tamanho.

Durante a execução do processo, o processo terá páginas de memória com quadros nas partes que estão ativas na memória principal. As partes que estão inativas estarão guardadas em páginas cujo quadros são da memória secundária. Fica a cargo do S.O carregar e descarregar as páginas da memória principal para a memória secundária e vice-versa.

Quando um novo processo chega, ele tem o seu tamanho analisado em páginas. Dessa forma, o sistema operacional sabe quantos quadros precisam estar disponíveis para aquele processo ser alocado. Para saber quantos quadros livres tem, o sistema operacional mantém uma lista de quadros livres. Por serem do mesmo tamanho e não ter mais a necessidade de ser contíguo, não importa a ordenação da lista.

Para realizar a proteção desses quadros, dentro da tabela de mapeamento de páginas, há a presença de um bit que determina se aquele mapeamento é valido ou inválido. Caso seja inválido, ele não será acessado.

As páginas são carregadas conforme a necessidade, ou seja, somente a página inicial do processo é carregada na memória. Depois disso, só são carregados na memória depois que são referenciadas. Para fazer isso, sempre que uma página é requerida e não está alocada à um quadro real, uma exceção de `page fault` é lançada. Essa interrupção causa o carregamento da página.