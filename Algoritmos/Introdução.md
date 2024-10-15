Algoritmos são um conjunto de passos finitos e bem determinados que nos permitem realizar uma determinada tarefa com sucesso. Esses passos podem ser divididos em módulos ou subprogramas para diminuir a complexidade do algoritmo. Dessa forma, além de diminuir a complexidade do algoritmo e facilitar a sua compreensão, algumas partes podem ser reutilizadas em outros algoritmos.
Ademais, algoritmos podem ser analisados quanto ao seu tempo de execução e, também, uso de memória. Um bom algoritmo é aquele que realiza a sua tarefa utilizando a menor quantidade de memória e tempo de execução possível. Portanto, saber analisar um algoritmo e determinar sua "qualidade" torna-se essencial para construir um algoritmo eficiente.
Um algoritmo só é dito correto quando, para toda entrada dada a ele, ele pare de executar quando a resposta correta for atingida e retornada.
## Complexidade
A complexidade de um algoritmo está intimamente associada com a quantidade de situações diferentes que aquele algoritmo precisa tratar. Por sua vez, a quantidade de situações que um algoritmo precisa tratar depende da complexidade do problema apresentado. Portanto, podemos concluir que a complexidade de um algoritmo é proporcional a complexidade do problema que é apresentado.
Para diminuir essa complexidade, podemos dividir o problema maior em problemas menores e tratá-los com sub rotinas no código. As sub-rotinas também tem uma complexidade menor e são mais fáceis de serem compreendidos, pois tratam problemas menores. Por fim, podemos unir as sub-rotinas para resolver o problema maior.
## Técnica de Decomposição de Problemas
Para decompor um problema em partes menores, podemos utilizar a abordagem top-down. Para fazer isso, existem 4 etapas:
- Dividir o problema em suas partes principais.
- Analise a divisão obtida para garantir coerência.
- Se alguma parte ainda estiver complexa, volte para a parte 1.
- Analise o resultado obtido para garantir coerência.
## Eficiência 
A Lei de Moore dita que o poder computacional dobra a cada 18 meses. Entretanto, os problemas crescem mais rápido que isso. Portanto, mesmo com o aumento do poder computacional, não é possível resolver esses problemas com uma velocidade imensa. 
A eficiência de um algoritmo está diretamente relacionada aos seguintes recursos:
- Quantidade armazenamento utilizada.
- Quantidade de throughput utilizado.
- Quantidade de dados movidos em disco.
## Problemas NP-Completos
Um problema é dito NP-Completo quando a sua execução correta, entretanto, a determinada execução demora muito tempo para ser completa. Dessa forma, ainda não há uma solução que determine a resposta correta com demanda de recursos e tempo de execução eficientes.
## Análise
Para realizar uma análise agnóstica de máquina, devemos nos concentrar no número de operações realizadas em função do tamanho da entrada dos elementos. O tamanho da entrada é associado aos parâmetros fornecidos na chamada inicial do algoritmo. Nesse caso, pode ser a quantidade de itens dentro de um arranjo, uma árvore