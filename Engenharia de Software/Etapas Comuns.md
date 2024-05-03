O Engenhero de Software precisará analisar e definir qual o processo de desenvolvimento que será adotado para o projeto de software. Inicialmente, terá que identificar  quais as atividades que irão compor o desejado processo e, em seguida, o fluxo do mesmo.

Geralmente, qualquer modelo de engenharia de software tem as seguintes etapas:
- Levantamento de Requisitos.
- Análise.
- Projeto.
- Implementação.
- Testes.
- Implantação.
### Levantamento de Requisitos 
O levantamento de requisitos é o primeiro passo a ser realizado. Essa etapa é essencial para entender o problema. Para fazer isso, ele terá que entrar em contato com quem sabe do negócio para poder entender o problema completamente. Isso pode exigir entrar em contato com vários usuários de diversas formas. Após esse contato, o engenheiro deve ser capaz de estipular os requisitos para que um determinado software resolva aquele problema.

Um requisito é a descrição de um serviço fornecido pelo sistema e suas restrições operacionais. Qualquer requisito reflete diretamente ou indiretamente a necessidade para solucionar um problema. Ainda assim, existem mais classificações dentro de requisitos:
- Funcionais:  Funcionalidades que estarão disponíveis no software final.
- Não Funcionais: Geralmente, são funcionalidades que estão relacionadas aos requisitos funcionais, mas não impactam no funcionamento da funcionalidade para o usuário, como sistema gerenciador de banco de dados, linguagem de programação e etc.
- Domínio: São as restrições aplicadas ao requisito funcional. Por exemplo, um requisito funcional é o cálculo de média e, um exemplo de restrição de domínio é que só deve ser calculada no final de mês.

Essa etapa produz um resultado que é chamado de `Escopo`. Esse escopo deve ser avaliado pelos usuários ou quem está pagando aquele sistema para poder ser validado e, também, ter seus defeitos apontados.
### Etapa de Análise
Depois da etapa de levantamento de requisitos, temos a etapa de análise. Com o documento de escopo em mãos, pode-se começar a ser analisado o que é necessário para que tais requisitos sejam atendidos. Para fazer isso, é produzido oque é chamado de `modelo`. 
O modelo é uma representação da solução de um ou vários problemas. No geral, eles fornecem uma determinada visão sobre aquele problema. Cada modelo apresenta com mais ênfase determinados pontos de vista. Nessa etapa, nenhuma restrição tecnologica é considerado, pois é uma abstração de alto nível.

> As duas principais vantagens dos modelos são: facilidade de correção e facilitação no entendimento entre partes técnicas e não técnicas.

Existem diversos modelos e cabe ao Engenheiro responsável à estabelecer o que é necessário ou não para aquele projeto.
### Etapa de Projeto
Essa etapa tem como entrada as análises e requisitos do usuário. Nesse ponto, será diminuido o nível de abstração e começará a ser levado em consideração questões mais próximas a implementação real. No final, será produzido um resultado no qual o sistema pode ser implementado a partir dele.

Portanto, essa etapa englobara o refinamento técnico e se preocupará com o "COMO" algo será feito. 
### Etapa de Implementação
Nessa etapa, ocorre a implementação de fato do produto, ou seja, escrita de código. Aqui, por exemplo, será consideração padrões de projeto para implementar aquele determinado software.
### Etapa de Testes
Nessa etapa, são aplicados os testes de software ou testes de validação que permitem verificar se o funcionamento está como o esperado. Esses testes podem validar os componentes individuais e/ou a integração entre eles. Portanto, aqui veremos testes de integração, unitários, testes de aceitação e etc.
### Etapa de Implantação
Nessa etapa, o software é migrado para o ambiente de produção.
## Fluxo de Processo
Depois de que cada etapa do processo é definida, é necessário ser definido um fluxo. Um fluxo diz respeito sobre em que ordem cada processo será executado, ou seja, trata diretamente sobre o encadeamento entre processos. Existem alguns tipos de fluxo:
- Linear: Cada atividade é executada somente uma vez e de maneira linear.
- Iterativa: Cada atividade é executada uma ou mais vezes antes de prosseguir para a próxima etapa.
- Evolucionário: Cada iteração é composta por todos os processos. No final dessa iteração, produz-se uma versão e, ao final dela, retorna ao começo.
- Paralelo: Um ou mais processos podem ser executados em paralelo.
- Iterativo e Incremental: Esse tipo é uma mistura de iterativo e evolucionário. Nesse caso, separa-se uma parte dos requisitos e ocorre um fluxo completo sobre eles. Depois disso, retorna-se ao início e segue ao próximo conjunto de requisitos.