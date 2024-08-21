## Problema
Cliente tentou realizar alteração na ordem e/ou zerar a posição, mas o sistema apontou limite insuficiente.
## Debbuging
A validação ocorre dentro de `RequireLimitDiff.cs` no método `public static RiskValuationResult ValidateAsClient(IPolicySearchService policySearchService, ClientContext context)`.
- Nesse caso, o limite disponível é calculado de acordo com o tipo de mercado se for VIS ou FRA, ele retorna o LimitPositionD2. Se não, ele retorna LimitPositionD1.
- No caso do cliente, o limite disponível foi o LimitPositionD1, pois o market era FUT. O valor dele era -568.3778
	- Para recuperar o Market, você pode olhar no Hist. Validações dentro de Relatórios, fazer a busca com os dados do cliente ou ordem. Em seguida, só clicar no ID que você irá para página com o Context daquele cliente.
- Depois de recuperar essa informação, o limite disponível do LimitPositionD1 foi somado ao `unusedOldOrderLimit`.
	- Para calcular esse unused, fazemos esse cálculo: `oldOrder.OrderLeaves * oldOrderPrice * contractMultiplier * currencyFactor;`
	- 4 * 5482 * 10 * 1 = 219,280 (NOVA ORDEM)
	- 4 * 5470 * 10 * 1 = 218,800 (ANTIGA ORDEM)
	- 218,800 + (-568.3778) = 218,231.62

Segundo a análise feita no Risco, verificamos que os valores estão corretos.   valor da nova ordem que foi enviado para alteração é calculado utilizando a seguinte regra: quantidade de ordem * o novo preço da ordem * multiplicador de contrato * currency factor. Os dados que coletamos foram os seguintes:
- Quantidade de Ordem: 4 
- Preço: 5482
- Multiplicador de Contrato: 10
- Fator da Moeda: 1 
Realizando a conta, chegamos ao resultado 219.280,00. Esse é o limite que ele precisa para realizar a alteração de ordem. 

O limite disponível é calculado com base na seguinte conta: LimitPositionD1.BasicLimit + UnusedLimit da Antiga Ordem. O UnusedLimit da Antiga ordem é calculado da seguinte forma: OldOrder.OrderLeaves * OldOrder.Price * contract multiplier (10) * currency factor (1). Dessa forma, chegamos a esse resultado: (-568.3778) + (4 * 5470 * 10 * 1)  = 218,231.62 . Desta forma, a nova ordem possui o valor 219.280,00 foi rejeitado por estar acima do limite disponível. 

Esses resultados foram provenientes da análise da validação da ordem de ID fcac6515
