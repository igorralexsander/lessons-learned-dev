# Event Driven

## Mensagem, Evento, Comando
* Mensagem: Genérica, sem intenção especifica
* Comandos: Algo que deve acontecer, futuro.
* Eventos: Algo que ja aconteceu, passado.

## Comando
Uma mensagem que é um comando, tempos uma aplicação que envia um comando para uma unica aplicação cpnsumidora,
o comando pode ser acatado ou não pela aplicação comandada (exemplo: DebitarConta, podemos ter inumeras situações
para que determinados comandos sejam inviabilizados de efetivar a solicitação). Frequentemente o processamento de
um comando pode gerar eventos (exemplo: SaldoInsuficiente, ContaDebitada)
* Quando temos um comando, o schema da mensagem sempre é definido pela aplicação a ser comandada.
* Apenas uma aplicação faz a leitura da mensagem.

## Evento
Uma mensagem do tipo evento, temos um evento relevante ao dominío da aplicação (um acontecimento imutavel), sempre 
referenciamos ao avento no passado (exemplo: PedidoRealizado, PedidoCancelado).

* Em uma mensagem do tipo evento, o schema da mensagem sempre é definido pelo produtor do evento.
* Permite que múltiplos interessados leiam o mesmo evento.