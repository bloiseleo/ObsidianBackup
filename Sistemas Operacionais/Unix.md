## História
O Unix nasceu como uma sistema operacional multitarefa baseado no Multics dentro da Bell Labs. Ele foi escrito primeiro em assembly e, posteriormente, em C. O seu grande sucesso veio por causa da facilidade de transportar o sistema operacional entre computadores diferentes. 

Com o passar do tempo, diversas variantes do Unix surgiram. Entretanto, todas elas mantiveram uma base de conceitos bem parecida com o Unix original. Por conta disso, nos dias de hoje, Unix é o nome dado à uma família de sistemas operacionais que seguem os mesmos conceitos e convenções estabelecidos por esses computadores.

## Estrutura
O Unix é estruturado em `Núcleo` ou `Kernel` e `Programas de System` . O `Kernel` roda em espaço de memória privilegiado e tem acesso direto ao Hardware e suas funções. Ele possui uma série de funções que são utilizados por programas com menos privilégio poderem executar alguma função. Essas funções são chamadas de chamadas de sistema e são disponibilizadas por bibliotecas em C.