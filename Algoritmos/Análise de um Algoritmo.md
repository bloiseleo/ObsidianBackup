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
- Best Case: A condição que gerá o melhor resultado em termos de eficiência. Nesse caso, estamos falando da Notação Omega (**Ω**). Nesse caso, por exemplo, quando dizemos que temos o resultado de tempo para 100 segundos, queremos dizer que o mínimo de tempo para que aquele algoritmo complete a sua tarefa é 100 segundos. Ele pode levar mais tempo, porém não levará menos tempo que isso.
- Average Case: A condição que gerá um resultado médio em termos de eficiência. Nesse caso, estamos falando da Notação Theta (**θ**). Nesse caso, ele determina a média de tempo ou espaço que um algoritmo irá levar para concluir essa tarefa.
- Worst Case: A condição que gerá o pior resultado em termos de eficiência. Nesse caso, estamos falando da Notação Big O (**O**). Nesse caso, ele determina a quantidade máxima de tempo ou espaço que um algoritmo irá levar para concluir a sua tarefa. Portanto, esse algoritmo pode levar menos ou exatamente o tempo dessa fórmula, mas nunca mais que isso.

### Notação Big O 

Existem algumas regras para essa notação:

- O processo está sendo executado em somente 1 processador.
- O processador executa uma ordem de cada vez sequencialmente.
- Operação de reservar espaço de memória, retornar um valor de uma função, operações aritméticas, operações lógicas  e qualquer outra operação simples e pequena consome 1 unidade de tempo (pode ser segundo, milisegundo e etc).
- Deve ser considerado somente o fator que mais afetara o resultado do tempo. Por exemplo, `T = n^2 + 3n + 1`. Nesse caso, podemos desconsiderar o `3n`e o `+ 1`, visto que o que mais influenciará é o `n^2`.
- Outro ponto, devemos ignorar multiplicadores constantes do n. No exemplo acima, podiamos excluir o `3`de `3n`.

Com base nessas regras, temos algumas notações que sempre aparecem:

- O(1): Tempo ou memória constantes de acordo com o crescimento do input. Esse é o caso ideal que sempre buscamos. Funções matemáticas e acessar índices possuem essa notação.
- O(n): Tempo ou memória crescem de acordo com o crescimento do input. Esse é um caso onde temos um for-loop que percorre todo um array, por exemplo, para achar um determinado dado. Nesse caso, teremos essa notação, visto que, no pior caso, o último elemento é o elemento procurado. Por conta disso, será necessário percorrer todo o array até achar o elemento.
- O(n^2): Tempo ou memória crescem de acordo com o quadrado do input. Esse caso é um onde queremos evitar a todo custo, visto que o seu crescimento é exponencial. 
- O(log n): Tempo ou memória crescem de acordo com o logaritmo do input na base 2. Esse caso é um lugar onde podemos estar, visto que ele, por vez, é até melhor que o O(n).