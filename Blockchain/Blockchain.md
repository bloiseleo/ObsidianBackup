A blockchain teve seu conceito criado em 1991 é um livro de registros que contêm informações sobre transações. Essas transações, uma vez gravadas, são imutáveis e confiáveis. Para alcançar esse objetivo, duas técnicas são utilizadas: redes e criptografia.

> As informações que são guardadas na blockchain pode ser qualquer uma. 

### Como funciona

A blockchain contêm informações sequenciais e temporais, ou seja, os blocos são mostrados na ordem em que são inseridos, onde cada bloco aponta para o anterior. 

Essa blockchain é composta por uma rede `peer-to-peer` onde cada nó (computadores conectados a rede) contém uma cópia local dos dados. Cada nó está conectado ao outro e, através de um algoritmo de consenso, podemos verificar se os dados estão válidos.

### Bloco
O bloco contém um hash que o indentifica e uma referência ao hash do bloco anterior. Dessa forma, cada bloco da blockchain está conectado através desse hash. O único bloco que não possui o hash anterior é o primeiro bloco da cadeia.  O Hash é gerado de acordo com todo o conteúdo do bloco: payload, data e hora e hash prévio.

> Além dessas informações, temos o `timestamp`, que serve como um carimbo de data e hora de quando aquela transação foi realizada.


