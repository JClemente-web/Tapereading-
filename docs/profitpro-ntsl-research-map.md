# Mapa de Pesquisa ProfitPro, NTSL e Automação

## Objetivo

Mapear tudo que precisa ser investigado na documentação do ProfitPro/Nelogica antes de implementar a automação. A regra é simples: o que for operar dinheiro precisa ter fonte funcional, teste, fallback e limitação conhecida.

## Áreas obrigatórias de pesquisa no ProfitPro

### 1. Editor de Estratégias

Fonte funcional: documentação Nelogica do Editor de Estratégias.

Pontos a confirmar:

- criação de estratégias em NTSL;
- tipos de estratégia;
- estratégias de execução;
- backtest;
- automação;
- slippage em ticks;
- quantidade de contratos;
- compilação;
- estatísticas;
- limitações por plano/versão.

Por que usar:

- é o caminho nativo para transformar regra em automação dentro do Profit.

Riscos:

- nem todo dado visual do Profit pode estar disponível diretamente em NTSL;
- funções podem depender de versão;
- execução real pode divergir de backtest.

### 2. Automação de Estratégias

Pontos a confirmar:

- como iniciar/parar automação;
- como configurar ativo;
- como configurar conta;
- como configurar quantidade;
- como tratar rejeição;
- como monitorar ordens pendentes;
- como bloquear reentrada;
- como zerar posição;
- como pausar após perda/ganho.

Uso no projeto:

- motor de execução;
- motor de bloqueio;
- kill switch;
- auditoria operacional.

### 3. NTSL

Pontos a confirmar:

- funções de compra e venda;
- funções de fechamento de posição;
- funções de posição atual;
- ordens stop/limit/market;
- OCO;
- leitura de volume;
- leitura de preço;
- leitura de indicadores;
- múltiplos ativos;
- logs/plots/debug;
- limitações com Times & Trades, DOM e Tape Reading.

Uso no projeto:

- implementação das regras;
- validação de confluências que estão disponíveis programaticamente;
- fallback para dados indisponíveis.

### 4. OCO e estratégias de saída

Fonte funcional: documentação Nelogica de Ordens OCO.

Pontos confirmados pela documentação:

- gain pode ser definido em ticks, financeiro ou percentual;
- loss pode ser definido em ticks, financeiro ou percentual;
- stop offset define ticks adicionais para execução da ordem stop;
- há suporte para saídas parciais em ticks;
- após posição encerrada, ordens gain/loss são canceladas simultaneamente;
- rejeições de OCO precisam ser tratadas.

Uso no projeto:

- proteção inicial;
- parcial;
- break-even;
- stop técnico;
- fallback de zeragem.

### 5. Tape Reading no ProfitPro

Pontos a pesquisar:

- quais dados do plugin são apenas visuais;
- quais dados podem virar regra NTSL;
- como usar alarmes;
- como capturar saldo de agressão;
- como mapear players;
- como usar Footprint;
- como usar Histograma de Agressão;
- como usar Times & Trades;
- como usar Volume At Price.

Uso no projeto:

- confluências de entrada;
- filtros de absorção;
- filtros de exaustão;
- player tracking;
- replay operacional.

### 6. Estratégias de múltiplos ativos

Pontos a confirmar:

- como NTSL acessa dados de outro ativo;
- como sincronizar WDO e WIN;
- como monitorar DOL, IND, ações líderes ou índices externos, se disponíveis;
- impacto no backtest;
- limitações de performance.

Uso no projeto:

- filtro de correlação;
- bloqueios macro;
- confirmação contextual.

## Matriz de disponibilidade

| Dado | Uso | Status inicial | Ação necessária |
| --- | --- | --- | --- |
| Preço | entrada, saída, alvo, stop | confirmado em plataforma | confirmar função NTSL específica |
| Volume | filtro de força | confirmado em plataforma | confirmar função NTSL específica |
| VWAP | contexto | confirmado em plataforma | confirmar implementação NTSL |
| Saldo de agressão | delta/contexto | funcional no Profit | confirmar acesso programático |
| Times & Trades | player/agressor | funcional no Profit | confirmar acesso programático/exportação |
| DOM/book | liquidez/wall | funcional no Profit | confirmar acesso programático/exportação |
| Volume At Price | zonas/POC | funcional no Profit | confirmar acesso programático |
| Notícias | bloqueio macro | externo/Profit | definir fonte e integração |
| Players | big players | funcional no Profit | confirmar granularidade e acesso |

## Decisão arquitetural provisória

A automação deve ser desenhada em duas camadas:

1. **Camada nativa Profit/NTSL**: execução, proteção, regras que usam dados disponíveis nativamente.
2. **Camada de pesquisa/auditoria externa**: logs, replay, análise estatística, notícias, investigação, relatórios e dados que não forem acessíveis diretamente em NTSL.

## Critério para implementar uma regra

Uma regra só pode ir para NTSL quando:

- a fonte funcional confirmou que o dado existe;
- a função ou caminho de acesso foi identificado;
- o comportamento em backtest foi testado;
- o comportamento em automação simulada foi testado;
- a proteção foi testada;
- a regra de bloqueio foi testada;
- o log registra entrada, saída e motivo.
