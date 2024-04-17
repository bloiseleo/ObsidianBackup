A programação orientada a aspecto, atualmente, é utilizada em conjunto com outros paradigmas. Esse paradgima se foca em reduzir a duplicidade do código quanto aos requesitos não-funcionais da aplicação, como logar determinadas informações durante uma ação. Nesse caso, ela encapsula em determinados conceitos essas ações e as executa conforme o programado.

### Como funciona?
Na _POA_, temos a construção de aspectos, que são a união e separação dos pontos acima, isolados. Nesse caso, esse aspecto pode modificar o comportamento de um código existente através de comportamentos adicionais chamados de `advices` em cima de um ponto de execução `join point`. A descrição lógica de um `join point` é chamado de `pointcut`

### AspectJ
Esse framework java é o responsável por aplicar esses conceitos. Nesse caso, temos que entender o seguinte: Ele define pontos de atuação. Esse ponto de atuação define um momento de interesse. Nesse caso, pode ser uma chamada de método, construtor, exceção lançada e etc. 

Dentro desse ponto de atuação, determinamos `advices`, que são códigos que, de fato, irão ser executados nos momentos de interesse. 

Acredito que com um exemplo ficará mais claro. Tenhamos a classe abaixo:

```
package app;

import java.math.BigDecimal;
import java.time.LocalDateTime;

public abstract class Account {
	private AccountKind kind;
	private ClientKind clientKind;
	private LocalDateTime openingDate;
	private BigDecimal saldo;
	public Account(
		AccountKind kind,
		ClientKind ckind,
		LocalDateTime openingDate,
		BigDecimal saldo
	) {
		this.kind = kind;
		this.openingDate = openingDate;
		this.saldo = saldo;
		this.clientKind = ckind;
	}
	protected BigDecimal zeroValue() {
		return BigDecimal.valueOf(0);
	}
	protected void checaValor(BigDecimal value) {
		if(value.compareTo(zeroValue()) <= 0) {
			throw new RuntimeException("Valor inválido " + value);
		}
	}
	public void sacar(BigDecimal value) {
		checaValor(value);
		BigDecimal restoSaldo = saldo.subtract(value);
		if(restoSaldo.compareTo(zeroValue()) < 0) {		
			throw new RuntimeException("Você não tem saldo suficiente");
		}
		saldo = restoSaldo;
	}
	public void depositar(BigDecimal value) {
		checaValor(value);
		saldo = saldo.add(value);
	}
	@Override
	public String toString() {
		var sb = new StringBuilder();
		sb.append(saldo);
		return sb.toString();
	}
}
```

No caso, vamos definir um ponto de ação no método sacar:
```
package app;

import java.math.BigDecimal;
import java.math.BigInteger;

public aspect AccountAspect {
	pointcut callSacar(BigDecimal saldo, Account acc): call(* Account.sacar(BigDecimal)) && args(saldo) && target(acc);
	before(BigDecimal saldo, Account acc): callSacar(saldo, acc) {
			System.out.println("Foi realizada uma tentativa de saque de " + saldo + " da conta " + acc);
	}
}
```

Nesse caso, definimos um ponto de interesse e chamamos ele de `callSacar`. Nesse caso, definimos que o ponto de junção no momento que o método `sacar` , é chamado de uma classe do tipo `Account` e que recebe um parâmetro do tipo `BigDecimal`. Logo, caso haja um overload de método, ele só irá pegar aquele que dá match exatamente.

Depois disso, adicionamos um advice `before`, que indica que é uma ação que será executada antes da execução do método. Dessa forma, conseguimos executar esse advice.