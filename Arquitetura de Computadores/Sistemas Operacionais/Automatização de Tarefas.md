Uma das principais funções que automatizam os nossos trabalhos é o CRON. Esse CRON é uma ferramenta que nos permite especificar comandos a serem executados em função de um intervalo de tempo pré-determinado. Todo comando dentro do CRON é executado como um processo no nível do usuário que o criou e cada usuário tem o seu.

Para criar o seu crontab ou editá-lo, você pode usar o comando `crontab -e`.  Cada tarefa é determinada em uma linha e somente uma linha. Esse comando aceita uma série de parâmetros que permite configurar o tempo em que será executado:

```
30 17 10 * * /bin/comando
```

No caso acima, o CRON será executado no dia 10 às 17:30.

O formato do tempo é o seguinte

Minuto -> 0 a 59
Hora -> 0 a 23
Dia -> 1 a 31
Mes -> 1 a 12
Dia da Semana -> 0 a 6

O CRON também aceita valores nos campos de data que sejam separados por vírgula ou traço. A vírgula indica valores específicos, ou seja, será executado quando um dos valores for atendido. O traço, por sua vez, indica intervalo.

O CRON também aceita rotinas que serão executadas globalmente, ou seja, definidas pelo `root` do sistema. Nesse caso, o arquivo é `/etc/crontab`. Além disso, também é possível especificar um usuário para essa tarefa da seguinte forma:

```
30 10 * * * root /bin/comando
```
