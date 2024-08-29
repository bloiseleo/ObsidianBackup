<<<<<<< HEAD
- Dentro da sprint:
	- Na sexta feira, passei com todos os tickets que tinha em review e somente o ticket RISK-1182 foi retomado para TO-DO, visto que o motivo pelo qual os pontos de impacto não estava presente na análise.
	- Agora, estou dando uma olhada no que o Fábio solicitou pelos comentários do ticket RISK-1182. Nesse caso, foi solicitado que fosse inserido um timer para medir o tempo dos requests no método GetOrDefault. Entretanto, ao tentar entender o método, vi que ele faz duas chamadas para o InternalGetOrDefault que, quando não tem os dados na memória ou ele está expirado, vai para o adapter buscar inforamção. Quando ele faz essa chamada, existe já um logger informando que o tempo de consulta do Adapter foi mto alto. A categorização de "alto"  é maior que 1000ms. Eu adiconei o timer da mesma forma que foi feito no método que busca os dados do adpater. Entretanto, ainda to em dúvida de como iremos testar. Além disso, também surgiu o questionamento se deveriamos diminuir o tempo do logger do adapter.  
- Fora da sprint: 
	- No caso, tiveram dois problemas para os quais eu gerei ticket: 
		- Falar sobre logout automático.
		- Alteração de ordem rejeitada por limite
=======
- Dentro da Sprint:
	- Consegui adicionar os logs, mas estou tendo problemas para colocar as aplicações compiladas dentro do ambiente de dev. No caso, ele dá 503 quando eu tento acessar pelo IIS, mas ele roda via console. Então, já coloquei o adapter para rodar via console e vou colocar o intelirisk para rodar via console também



## Pontos Positivos
## Pontos Negativos
- Mais clareza nos objetivos e descrição dos tickets.
>>>>>>> ac3af43c7694b79695064fbb7212609ed7a2c2f1
