Go é uma linguagem compilada, ou seja, todo código é convertido em código de máquina antes de ser executado. Para executar um projeto go, deve haver um `package` chamado de `main` e, dentro dele, ter uma função chamada de `main`. Logo, o `hello world` fica dessa forma:

```
package main

import "fmt"

func main() {
	fmt.Printf("Hello World!\n")
}
```

> Por padrão, golang sempre trata caracteres como UNICODE.

Caso queiramos executar a aplicação, podemos usar o comando `go run .` para executar o projeto acima. Entretanto, caso queiramos buildar o projeto, pode entrar dentro da pasta onde encontra-se o arquivo `go.mod`e executar `go build .` para realizar o build do binário do projeto. Dessa forma, é produzido um binário com o nome do modulo do projeto.

## Packages
A linguagem Go é organizada em pacotes. Nesse caso, um pacote é um diretório preenchido com arquivos `.go`. É recomendado que eles tenham uma relação lógica e façam um conjunto de tarefas que tenha a ver somente com aquela determinada tarefa.

Um package pode ser executável ou não. Para ele ser execuitável, deve haver um `package main`e, também, uma `func main`. Caso não tenha, ele é um `package` que ser como biblioteca.

> Todo arquivo em Go, no geral, será `package ... import...`, onde o import é a indicação de que determinado pacote está sendo utilizado.


## Import
Para determinar quais pacotes um determinado arquivo está utilizando, temos a palavra chave `import`. Essa palavra chave nos permite importar um pacote ou mais. Para fazer isso, fazemos da seguinte forma:

```
import "fmt"
```

Nesse caso, estamos importando um pacote chamado de "fmt". Para importar vários pacotes de uma vez só, podemos fazer o seguinte:

```
import (
	"fmt"
	"os"
	"strings"
)
```

