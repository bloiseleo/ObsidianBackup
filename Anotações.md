- Qual cliente a guide usa? 
	- Precisamos dessa informação para buscar as ordens nos logs.

## Link
http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/
#### INTELIORDER -> BOLSA
- [FIX.4.4-CGUI0044-OE205.event.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-CGUI0044-OE205.event.current.log)
- [FIX.4.4-CGUI0044-OE205.messages.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-CGUI0044-OE205.messages.current.log)
- [FIX.4.4-CGUIA823-OE066.event.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-CGUIA823-OE066.event.current.log)
- [FIX.4.4-CGUIA823-OE066.messages.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-CGUIA823-OE066.messages.current.log)
### Sessões de Repasse
#### INTELIORDER -> BOLSA (SESSÕES DE REPASSE DO OPERADOR)
- [FIX.4.4-RGUI0006-OE209.event.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-RGUI0006-OE209.event.current.log)
- [FIX.4.4-RGUI0006-OE209.messages.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-RGUI0006-OE209.messages.current.log)
- [FIX.4.4-RGUIA313-OE042.event.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-RGUIA313-OE042.event.current.log)
- [FIX.4.4-RGUIA313-OE042.messages.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-RGUIA313-OE042.messages.current.log)
#### VALEMOBI -> INTELIORDER
- [FIX.4.4-INTELIORDER_BOV_REPASSADOR-VALEMOBI_BOV_REPASSADOR.event.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-INTELIORDER_BOV_REPASSADOR-VALEMOBI_BOV_REPASSADOR.event.current.log)
- [FIX.4.4-INTELIORDER_BOV_REPASSADOR-VALEMOBI_BOV_REPASSADOR.messages.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-INTELIORDER_BOV_REPASSADOR-VALEMOBI_BOV_REPASSADOR.messages.current.log)
- [FIX.4.4-INTELIORDER_BMF_REPASSADOR-VALEMOBI_BMF_REPASSADOR.event.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-INTELIORDER_BMF_REPASSADOR-VALEMOBI_BMF_REPASSADOR.event.current.log)
- [FIX.4.4-INTELIORDER_BMF_REPASSADOR-VALEMOBI_BMF_REPASSADOR.messages.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-INTELIORDER_BMF_REPASSADOR-VALEMOBI_BMF_REPASSADOR.messages.current.log)
- [FIX.4.4-INTELIORDER_BMF_DMA-VALEMOBI_BMF_DMA.event.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-INTELIORDER_BMF_DMA-VALEMOBI_BMF_DMA.event.current.log)
- [FIX.4.4-INTELIORDER_BMF_DMA-VALEMOBI_BMF_DMA.messages.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-INTELIORDER_BMF_DMA-VALEMOBI_BMF_DMA.messages.current.log)
- [FIX.4.4-INTELIORDER_BOV_DMA-VALEMOBI_BOV_DMA.event.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-INTELIORDER_BOV_DMA-VALEMOBI_BOV_DMA.event.current.log)
- [FIX.4.4-INTELIORDER_BOV_DMA-VALEMOBI_BOV_DMA.messages.current.log](http://d3pwapitdoms001.guide.com.br:9090/InteliOrder/quickfix/log/FIX.4.4-INTELIORDER_BOV_DMA-VALEMOBI_BOV_DMA.messages.current.log)
	- Ordens são enviadas para o inteliorder nessa secção e são enviadas para a bolsa.

## Execution Report
Estamos procurando por Execution Reports de rejeição que indiquem algum mal funcionamento da aplicação.
#### Passo a Passo
- A ordem saiu da Valemobi e foi para o Order?
- A ordem que passou da order foi validada pelo risk? (Ver no log do Risk e InteliOrder app)
- Conseguimos mandar a ordem para a bolsa depois de validar? (Ver no log fix)
- A bolsa vai responder essa ordem pro InteliOrder e precisamos repassar essa mensagem para a valemobi. (Ver no log da sessão que enviou a ordem).
### TUDO OK 
- Orders may not be entered while the market is forbidden (Mercado Fechado)
### PROBLEMÃO
- Faltando uma tag que é required.
- Dicionário desatualizado.
### Tipos de Reject

Link: https://www.b3.com.br/data/files/80/62/92/88/B11309105FE89209AC094EA8/EntryPointMessageSpecs2.35.pdf

BOV e BMF é tudo bolsa, mas a bolsa separa as ordens de acordo com o "tipo" do Ativo.

EQUITIES -> BOV
DERIVATIVES -> BMF

Para avaliar isso, pedir ao cliente quem mandou e qual foi o ativo.
![[image.png]]