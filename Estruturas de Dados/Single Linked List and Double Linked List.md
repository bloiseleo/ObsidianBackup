Uma lista ligada é muito parecida com uma lista, onde cada item da lista possui, pelo menos, um ponteiro para o próximo elemento da lista, que também possui dados. O final da lista é representado quando o próximo nó é `null`e, o início da lista (listas duplamente ligadas), é quando o nó anterior é `null`.

### Single Linked List
Uma lista ligada simples possui um ponteiro somente para o próximo elemento. Dessa forma, o primeiro nó deve ser armazenado. Caso ele seja perdido, toda a lista será perdida. O primeiro elemento da lista é chamado de `head`e, o último, é chamado de `tail`. 

A vantagem aqui é que podemos usar menos memória. Entretanto, percorrer a lista torna-se um problema, visto que só podemos percorré-la em um sentido. Nesse caso, se quisermos garantir que passaremos por todos os elementos, precisamos da referência ao começo da lista.
### Double Linked List
Uma lista duplamente ligada possui dois ponteiros: um para o elemento anterior e outra para o elemento posterior. Nesse caso, a partir de qualquer elemento, podemos chegar no começo ou no final. O primeiro elemento é chamado de `head`e o último é chamado de `tail`.

A vantagem aqui é que, a partir de qualquer elemento, podemos chegar no começo ou no final da lista. Por causa disso, conseguimos percorrê-la a partir de qualquer instância. Contudo, teremos que gastar o dobro de memória.