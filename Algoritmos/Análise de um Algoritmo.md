A análise de um algoritmo tem como objetivo analisar a quantidade de tempo e memória necessários para que determinado algoritmo resolva aquele problema.

### Time Complexity 
Essa medida é uma medida que determina quanto tempo um determinado algoritmo irá levar para ser concluído de acordo com uma determinada entrada.

Para determinar se um algoritmo é eficiente, ele deve ser comparado com outras soluções. Aquele algoritmo que levar a menor unidade de medida para o maior input, será considerado mais eficiente para resolução desses problemas.
### Space Complexity
Essa medida é uma medida que determina quanto de espaço um determinado algoritmo irá levar para ser concluído de acordo com uma determinada entrada.

Para determinar se um algoritmo é eficiente em uso de memória, ele deve ser comparado com outras soluções. Aquele algoritmo que levar a menor unidade de memória para a maior quantidade de input, será considerado o mais eficiente para resolução desse problema.

> Uma coisa que pode acontecer é: o melhor para espaço pode acabar consumindo mais tempo e vice versa. Nesse caso, cabe analisar melhor a sua solução e, por sua vez, selecionar o que melhor supre suas necessidades.

### Análise Assintomática
De fato, todos os aspectos do hardware influenciam na análise da eficiência de um algoritmo. Portanto, quando vamos fazer a análise, nós dizemos que vamos fazer a análise assintomática do mesmo. Nesse caso, analisamos somente as etapas que ele vai tomar e, também,  no tamanho da entrada e seu crescimento. Dessa forma, não importa o hardware que aquilo será executado e teremos uma ideia geral do desempenho do hardware.

Para fazer isso, usamos termos matemáticos que nos ajudam a descrever a performance de um algoritmo. Nesse caso, como estamos falando de análise assintomática, temos uma função cuja entrada será o input ou algo relacionado com ele e, a saída, seria o tempo e/ou a memória.

Além disso, existem algumas notações referentes aos diferentes contextos que aquele algoritmo é submetido:
- Best Case: A condição que gerá o melhor resultado em termos de eficiência..
- Average Case: A condição que gerá um resultado médio em termos de eficiência.
- Worst Case: A condição que gerá o pior resultado em termos de eficiência.