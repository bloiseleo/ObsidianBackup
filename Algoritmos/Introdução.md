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
Para realizar uma análise agnóstica de máquina, devemos nos concentrar no número de operações realizadas em função do tamanho da entrada dos elementos. O tamanho da entrada é associado aos parâmetros fornecidos na chamada inicial do algoritmo. Nesse caso, pode ser a quantidade de itens dentro de um arranjo, itens de uma árvore e etc.
Existem algumas atividades de um algoritmo que são considerados como passos básicos, ou seja, operações primitivas utilizadas pela máquina para realizar uma determinada tarefa:
- Operações aritméticas.
- Comparações.
- Atribuições.
- Resolver um ponteiro ou referência.
- Indexação de um array.
- Chamadas e retornos de funções e métodos.
Exemplo abaixo dos passos básicos:
```
int main(int* arr, int size, int v) {
	int achou = 0; // Passo básico 1
	for(int i = 0; i < size; i++) {
		if(arr[i] == v) { // Passo básico 2
			achou = 1; // Passo básico 3
			return achou; // Passo básico 4
		}
	}
	return achou; // Passo básico 5
}
```
### Tipos de Análise
Existem dois tipos de análise que podem ser realizados sobre algoritmos:
- Espacial: Analisa o espaço de memória consumido pelo algoritmo para executar o algoritmo.
- Temporal: Esse tipo de complexidade é o mais usado e pode ser dividido em dois grupos:
	- Tempo (real) necessário a execução do algoritmo.
	- Número de instruções necessárias à execução.

> A análise temporal é a mais usada. 
### Análise Assintótica
Nesse tipo de análise, deve-se considerar o tamanho da entrada para um algoritmo e levar em consideração os seguintes pontos:
- Cada operação (passo básico) leva o mesmo tempo constante.
- A memória da máquina é eficiente.
Por conta disso, o resultado dessa análise pode ser expressa como uma função `f(n)`, onde `n` é o tamanho da entrada da função que você deseja analisar. Portanto, essa análise determina a eficiência do algoritmo quando N torna-se grande. 

> Podemos entender que essa função basicamente determina o quanto de espaço e/ou tempo que esse algoritmo irá utilizar de acordo com o tamanho do input.

O resultado dessa análise assintótica é a complexidade assintótica do algoritmo para entradas suficientemente grandes. Logo, um algoritmo com complexidade assintótica medida é determinado como eficiente quando ele é eficiente para todas as entradas, com exceção de entradas pequenas.
### Comparação Assintótica
Quando temos duas complexidades assintóticas, a preocupação é a velocidade de crescimento do consumo de recursos e tempo daquele algoritmo. Logo, valores constantes que estão sendo multiplicados e/ou somados são ignorados, visto que eles afetam de modo irrelevante a velocidade do crescimento de consumo de recursos. Um exemplo: 10 x n cresce tão rápido quanto 100 x n. Logo, as multiplicações são ignorados. Contudo, n ^ 2 cresce bem mais rápido que n * 2. Logo, n é mais rápido que n^2.
Existe um certo padrão nas análises e valores que surgem. A ordem mais conhecida é a seguinte:
- Constante: f(1)
- Logaritmica: f(log n)
- Linear: f(n)
- Log linear: f(log n * n)
- Quadrática: f(n^2)
- Cúbica: f(n ^ 3)
- Exponencial: f(a^n)
- Fatorial: f(n!)
### Notação O (Big O)
A notação big O é a forma que a matemática denota o pior caso possível para um algoritmo. O pior caso é aquele onde uma maior quantidade de passos básicos é necessário para resolver um determinado problema.