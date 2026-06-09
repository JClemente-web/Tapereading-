# Blueprint de Automação Profissional no ProfitPro

## Posição do projeto

Este projeto não é um material de estudo e não é uma coleção de indicadores. O objetivo é especificar uma automação profissional para operar com capital real no ProfitPro, com regras objetivas, investigação rastreável, execução controlada, proteção automática, auditoria e bloqueios de risco.

A automação deve funcionar como uma mesa de execução disciplinada: ela liga, verifica se o ambiente está apto, monitora WDO e WIN, espera confluências, executa somente quando as regras estão completas, protege a posição, registra tudo e para quando as condições deixam de existir.

## Prioridade dos ativos

1. **WDO / Mini Dólar**: ativo principal.
2. **WIN / Mini Índice**: ativo secundário, usado com regra própria e com foco em movimentos mínimos de 500 pontos.

## Objetivos operacionais parametrizados

### WDO — Scalp 4 Pontos

- Meta por operação: 4 pontos.
- Meta diária planejada: 2 operações de 4 pontos.
- Total diário planejado: 8 pontos.
- Tick oficial: 0,5 ponto.
- Valor por tick: R$ 5,00 por contrato.
- Valor por ponto: R$ 10,00 por contrato.
- 4 pontos: R$ 40,00 por contrato.
- 8 pontos: R$ 80,00 por contrato.

### WIN — Movimento mínimo de 500 pontos

- Movimento mínimo de interesse: 500 pontos.
- Tick oficial: 5 pontos.
- Multiplicador oficial: R$ 0,20 por ponto.
- 500 pontos: R$ 100,00 por contrato.
- Após deslocamento mínimo favorável, o sistema deve priorizar proteção da posição.

## Fontes oficiais usadas para os parâmetros

- B3 — Mini U.S. Dollar Futures: especificação do WDO, ticker, tamanho do contrato, cotação, tick size e lote mínimo.
- B3 — Futuro de Ibovespa: especificação do WIN, horário, multiplicador, tick size e lote mínimo.
- B3 — Minimum Tick Sizes: confirmação dos tick sizes WDO = 0,5 e WIN = 5.
- Nelogica — Editor de Estratégias: NTSL, backtest e automação de estratégias no Profit.
- Nelogica — Ordens OCO: gain, loss, stop offset, saídas parciais e comportamento das ordens vinculadas.

## Arquitetura profissional

```text
Fontes e pesquisa
  -> Camada de dados
  -> Classificador de regime
  -> Motor de confluências
  -> Motor de decisão
  -> Motor de execução
  -> Motor de proteção
  -> Motor de bloqueio
  -> Auditoria e replay
  -> Relatório de performance
```

## Camada de dados

A automação deve observar, conforme disponibilidade no ProfitPro/NTSL e integrações complementares:

- preço atual;
- candles e periodicidades configuradas;
- agressão compradora/vendedora;
- saldo de agressão;
- delta por janela;
- Volume At Price;
- VWAP;
- Times & Trades;
- ordem original;
- ranking de players;
- book/DOM;
- profundidade do book;
- notícias e calendário macro;
- ativos correlacionados.

Quando algum dado não estiver disponível programaticamente no NTSL, o requisito deve ser classificado como:

- disponível nativamente;
- disponível visualmente no ProfitPro;
- disponível via exportação;
- disponível via fonte externa;
- ainda não confirmado.

## Classificador de regime

Antes de qualquer entrada, a automação deve classificar o mercado.

Regimes mínimos:

- tendência de alta;
- tendência de baixa;
- lateralidade;
- abertura volátil;
- notícia iminente;
- pós-notícia;
- liquidez reduzida;
- fluxo climático;
- consolidação pré-rompimento;
- rompimento em andamento;
- exaustão;
- absorção;
- horário proibido.

Nenhuma regra de entrada deve ser avaliada sem regime definido.

## Motor de confluências

Uma entrada só pode ser habilitada quando houver confluências suficientes. Para WDO, uma entrada de scalp de 4 pontos deve exigir, no mínimo:

1. regime compatível;
2. direção definida ou setup de reversão validado;
3. agressão no lado da operação;
4. eficiência do fluxo ou absorção validada;
5. ausência de barreira relevante contra o alvo;
6. alvo técnico/volumétrico livre até 4 pontos;
7. stop técnico proporcional;
8. notícia não bloqueante;
9. limite diário ainda disponível;
10. risco operacional dentro do permitido.

## Motor de decisão

O motor de decisão deve ter três estados:

- **Bloqueado**: não pode operar.
- **Observando**: existem sinais, mas faltam confluências.
- **Armado**: todas as condições estão completas e a execução pode ocorrer quando o gatilho for acionado.

A automação nunca deve pular de “bloqueado” para “executar”. Ela deve passar por “observando” e “armado”, registrando o motivo da transição.

## Motor de execução

A entrada deve ser disparada apenas por regra objetiva.

Campos obrigatórios da ordem:

- ativo;
- direção;
- quantidade;
- tipo de ordem;
- preço de referência;
- alvo;
- stop;
- stop offset;
- horário;
- setup;
- confluências presentes;
- motivo da entrada;
- plano de proteção.

A execução deve respeitar:

- limite de quantidade por ativo;
- limite de operações por dia;
- limite de perda diária;
- limite de ganho diário;
- limite por horário;
- limite por rejeição de ordem;
- bloqueio pós-notícia;
- bloqueio por instabilidade ou dado ausente.

## Motor de proteção

Após entrada, a automação deve proteger a posição automaticamente.

Proteções mínimas:

- OCO inicial com gain e loss;
- stop offset parametrizado;
- stop técnico por invalidação;
- proteção em ponto de equilíbrio quando o deslocamento mínimo ocorrer;
- trailing ou proteção dinâmica conforme ativo;
- saída por fluxo contrário;
- saída por perda de eficiência;
- zeragem por notícia ou risco externo;
- zeragem por horário limite;
- zeragem por erro operacional.

## Regras de proteção por ativo

### WDO

O modo principal busca 4 pontos. A proteção deve avaliar:

- mover para defesa quando o preço andar a favor e o fluxo perder força;
- sair antes do alvo se o fluxo inverter com intensidade;
- não manter posição após invalidação da confluência original;
- bloquear nova entrada após atingir a meta diária ou após sequência de perdas definida.

### WIN

O modo principal busca no mínimo 500 pontos. A proteção deve avaliar:

- após avanço mínimo favorável, proteger parte relevante do movimento;
- evitar devolver movimento grande em reversões rápidas;
- bloquear operação em lateralidade estreita;
- exigir regime mais claro que no WDO, porque o alvo é maior.

## Motor de bloqueio

A automação deve bloquear entradas quando ocorrer qualquer condição crítica:

- notícia de alto impacto em janela proibida;
- spread anormal;
- book inconsistente;
- ausência de dados necessários;
- divergência entre fontes;
- slippage acima do tolerado;
- sequência de rejeições;
- perda diária atingida;
- ganho diário atingido;
- horário fora da janela operacional;
- limite de trades atingido;
- ativo em leilão ou condição especial;
- volatilidade incompatível com o setup;
- liquidez insuficiente para entrada e saída.

## Auditoria obrigatória

Cada decisão deve ser registrada, inclusive as decisões de não operar.

Campos mínimos:

- timestamp;
- ativo;
- regime;
- estado do motor;
- sinal detectado;
- confluências presentes;
- confluências ausentes;
- motivo de bloqueio;
- decisão tomada;
- ordem enviada ou não enviada;
- preço;
- alvo;
- stop;
- resultado;
- avanço favorável máximo;
- avanço contrário máximo;
- fonte dos dados usados.

## Critério de prontidão para capital real

A automação só pode ser considerada pronta para operação real quando:

1. as fontes estiverem mapeadas;
2. as regras estiverem documentadas;
3. as regras estiverem implementadas;
4. os backtests estiverem executados;
5. o replay estiver auditado;
6. a simulação em tempo real estiver validada;
7. as rejeições e falhas estiverem tratadas;
8. o plano de stop e proteção estiver testado;
9. o limite de risco estiver parametrizado;
10. houver relatório que justifique cada operação.

## Perguntas obrigatórias para cada regra

Toda regra precisa responder:

- **Onde** ela atua?
- **Como** ela detecta o contexto?
- **Por que** ela tem validade operacional?
- **Quando** ela deve operar?
- **Quando** ela deve bloquear?
- **Com quais dados** ela decide?
- **Com quais fontes** ela foi sustentada?
- **Qual é a invalidação?**
- **Qual é o plano de saída?**
- **Qual é o plano se a ordem falhar?**
