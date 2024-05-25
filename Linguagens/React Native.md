> É um framework javascript destinado para construção de aplicações mobile e web a partir de uma única base de código. Ele se utiliza dos conceitos do React, mas os aplica de maneira diferente do que na web. 

Dentro dos telefones do iOS, há uma engine que é responsável por executar o javascript. No caso do android, esse mesmo não existe. Para executar o aplicativo escrito em JS em android, você precisa levar junto uma engine que execute-o (que no caso vai junto com o react-native).

## Compilação
Quando o projeto é compilado, os arquivos JavaScript serão transformados em bundle pelo metro e, os arquivos nativos (java/c++), serão compilados. Cada um desses códigos serão organizado em um bundle executável daquela platforma.
## Execução
Em tempo de execução, o código nativo irá rodar dentro do dispositivo e, o código em javascript, irá rodar em uma outra thread dentro da JavaScript VM. Para que ambas se comuniquem, elas trocam informações entre si através de JSON e, também, a Bridge. Essa Bridge é outro conjunto de software que gerencia essa comunicação, mas é feita primordialmente através de JSON.

Quando o aplicativo iniciar, 3 threads serão iniciadas:
- Main Thread: Thread onde o aplicativo vai estar executando. Ela é responsável por lidar com eventos da UI e renderizá-la.
- Javascript Thread: Thread onde a VM está sendo executada com nosso código js.
- Shadow Thread: Thread onde as posições e views serão calculcadas tendo como entrada o output do react e transforma em algo que a Main Thread entende. Dessa forma, ela consegue renderizar nativamente. No React Native, quem faz isso, é o Yoga, que utiliza-se de um esquema basedo em flexbox.

A comunicação se dá dessa forma:
- Usuário executa ação que dispara um evento.
- Mensagem do evento é gerada e serializada e enviada para a bridge.
- A bridge envia a mensagem para a thread do javascript.
- O javascript deserializa, decide o que fazer e devolve para a bridge.
- A bridge envia a mensagem para a thread do aplicativo.
- O aplicativo aplica as ações.

## Componentes
Um componente é um conceito de interface máxima reduzidaa. Nesse caso, podemos imaginar o componente como a menor unidade de um componente visual.  Ela representa alguma determinada informação e possui sua própria estilização de modo independente. Os componentes podem ser encaixados um dentro do outro para formar componentes maiores.
### View
A partir disso, vamos construimos nossas telas. Para fazer isso, precisamos, primeiro, criar um container que irá conter nossos elementos. O React Native chama esse componente de `View`, que é o mais básico de todos. Ele será traduzido para diferentes coisas no nativo. Dessa forma, a  mais básica é:

```
<View>
	<Text>Hello World!</Text>
</View>
```

Para podermos lidar com eventos relacionados com essa `View`, podemos lançar mão dos eventos. Geralmente, eles começam com `on` e a continuação desse nome é relacionada a açao que o dispara. Por exemplo, para lidar com o clique do usuário, podemos fazer da seguinte forma:
```
    <View onTouchStart={() => {
      console.log("clicked!");
    }}
    onTouchEnd={() => {
     console.log("ended!");
    }}>
    ...
    </View>
```
Nesse  caso, `TouchStart` é emitido quando o usuário clica na tela. `TouchEnd` é emitido quando o usuário termina de clicar na tela.
