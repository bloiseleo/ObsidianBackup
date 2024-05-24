O SQL apresenta uma determinada categoria de comandos que engloba comandos que realizam um determinado conjunto de operações. Nesse caso, existem os seguintes:
- DDL: Definition Data Language.
- DCL: Data Control Language.
- DML: Data Manipulation Language.
- TCL: Transaction Control Language.
- DQL: Data Query Language.

## DQL
O data query language é um conjunto de comandos que trata sobre a consulta de dados. Para realizar a consulta, usamos o comando `SELECT`. Esse comando seleciona dados da tabela dentro do banco de dados. Nesse caso, poedmos pegar todos os dados ou somente alguns deles. A sintaxe básica é: `SELECT nome_dos_campos FROM nome_da_tabela`. Nesse caso, caso queira todos os campos, podemos usar o `*`.  

Um exemplo é de um banco de dados cujos dados foram salvos dentro de uma tabela chamada `clientes`. Para recuperar todos os campos, podemos usar a seguinte query:

```
USE nome_do_banco;
SELECT * FROM clientes;
```

Ainda dentro de `SELECT`, podemos ordernar os resultados desse comando de acordo com um dado de uma tabela. Por exemplo, para ordenar por nome, adicionamos, no final da query, o comando `ORDER BY nome_da_coluna`. Esse comando irá ordenar os resultados do `SELECT` com base na coluna selecionada. Ainda assim, podemos escolher se será crescente ou decrescente com `ASC` ou `DESC`.

Por exemplo, para consultar os clientes e ordernar pelo nome, realizamos a seguinte consulta:

```
SELECT * FROM clientes ORDER BY name DESC;
```

Nesse caso, ele recupera os clientes e ordena eles pelo nome. Caso você queira que ordene com base em várias colunas, você pode usar o seguinte SQL:

```
SELECT * FROM clientes ORDER BY name DESC, surname ASC;
```

Nesse caso, primeior, ele ordena por `name` e, depois, por `surname`.
## DML
O data manipulation language é um conjunto de comandos que trata sobre manipular os dados, ou seja, criar, inserir e deletar.
## DDL
O data definition language é um conjunto de comandos que trata sobre a definição de dados, ou seja, criação de tabelas, bancos de dados e etc.
- `CREATE`: Esse comando nos permite criar alguma coisa dentro do nosso banco de dados.
	- Para criar um banco de dados, podemos executar `CREATE DATABASE nome_do_banco` para termos a criação dele.