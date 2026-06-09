# Referências e Evidências do Projeto

## Objetivo

Este arquivo organiza as referências que sustentam a evolução profissional da ferramenta de Tape Reading para WDO. A função dele é separar:

- fonte oficial;
- fonte funcional da plataforma;
- referência acadêmica;
- hipótese operacional do projeto;
- ponto que ainda precisa ser validado com dados.

## Referências oficiais e funcionais

### B3 — Mini U.S. Dollar Futures

- Link: https://www.b3.com.br/en_us/products-and-services/trading/exchange-rates/mini-u-s-dollar-futures.htm
- Tipo: fonte oficial do produto negociado.
- O que sustenta no projeto:
  - ticker WDO;
  - tamanho do contrato de USD 10.000;
  - cotação em BRL por USD 1.000;
  - tick size de BRL 0,5 por USD 1.000;
  - lote mínimo de 1 contrato.
- Como influencia o produto:
  - cálculo de pontos, ticks e valor financeiro;
  - painéis de objetivo operacional;
  - normalização de volatilidade;
  - módulo de gestão de risco.
- Limitação:
  - a página define especificações contratuais, mas não define setups, probabilidade operacional ou parâmetros de Tape Reading.

### Nelogica — Plugin Tape Reading

- Link: https://ajuda.nelogica.com.br/hc/pt-br/articles/360055004131-Plugin-Tape-Reading
- Tipo: documentação funcional da plataforma.
- O que sustenta no projeto:
  - existência do Gráfico Tape Reading/Footprint;
  - análise de ativos;
  - análise de players;
  - ranking de ativos;
  - indicadores de agressão;
  - alarmes de agressão;
  - periodicidades por volume e agressão.
- Como influencia o produto:
  - definição dos módulos que a nossa ferramenta deve complementar;
  - desenho da camada de alertas;
  - integração conceitual com fluxo, players e agressão.
- Limitação:
  - documentação de uso da ferramenta, não uma metodologia estatística de validação dos sinais.

### Nelogica — Gráfico Tape Reading / Footprint

- Link: https://ajuda.nelogica.com.br/hc/pt-br/articles/360061300911-Gr%C3%A1fico-Tape-Reading-Footprint
- Tipo: documentação funcional da plataforma.
- O que sustenta no projeto:
  - leitura de agressões por nível de preço dentro do candle;
  - conceito de agressor como participante que toma iniciativa com ordem a mercado;
  - parâmetros como fator de imbalance e fator sequencial.
- Como influencia o produto:
  - desenho de regras de imbalance;
  - separação entre agressão isolada e sequência de agressões;
  - criação de cenários simulados de footprint.
- Limitação:
  - não define quais parâmetros são melhores para WDO; isso precisa ser validado por contexto e estatística.

### Nelogica — Histograma e Saldo de Agressão

- Link: https://ajuda.nelogica.com.br/hc/pt-br/articles/360052485332-Tape-Reading-Histograma-e-Saldo-de-Agress%C3%A3o
- Tipo: documentação funcional da plataforma.
- O que sustenta no projeto:
  - uso de acumulado de agressão por período;
  - visualização de agressão positiva e negativa;
  - leitura de saldo como proxy de dominância de fluxo.
- Como influencia o produto:
  - modelagem de delta por janela;
  - modelagem de delta acumulado;
  - alertas de divergência entre preço e saldo.
- Limitação:
  - saldo de agressão sozinho não deve virar sinal de entrada sem contexto de preço e book.

### Nelogica — Alarmes de Tape Reading

- Link: https://ajuda.nelogica.com.br/hc/pt-br/articles/360049489432-Alarmes-de-Tape-Reading-Como-configurar-e-utilizar
- Tipo: documentação funcional da plataforma.
- O que sustenta no projeto:
  - existência de alarmes de Tape Reading no Gerenciador de Alarmes;
  - gatilhos relacionados a compra/venda, inversão, presença de player, algoritmo e saldo de agressão.
- Como influencia o produto:
  - criação do catálogo de alertas;
  - diferenciação entre alerta nativo e alerta contextual;
  - necessidade de reduzir falsos positivos por confluência.
- Limitação:
  - alarmes nativos são gatilhos; o projeto precisa transformá-los em contexto operacional validado.

### Nelogica — Times & Trades

- Link: https://ajuda.nelogica.com.br/hc/pt-br/articles/360054569632-Times-Trades
- Tipo: documentação funcional da plataforma.
- O que sustenta no projeto:
  - abas de negócios, ordem original, compradores, vendedores, saldo e evolução no tempo;
  - uso do Times & Trades para leitura de players e execução.
- Como influencia o produto:
  - modelagem de `Trade`, `PlayerActivity` e `AggressionSide`;
  - análise de players;
  - replay de eventos.
- Limitação:
  - depende da disponibilidade e estrutura dos dados acessíveis ao usuário.

### Nelogica — Volume At Price

- Link: https://ajuda.nelogica.com.br/hc/pt-br/articles/360047070932-Volume-At-Price
- Tipo: documentação funcional da plataforma.
- O que sustenta no projeto:
  - interpretação de volume de negócios por nível de preço;
  - identificação de faixas de defesa e posicionamento dos participantes.
- Como influencia o produto:
  - definição de zonas de liquidez;
  - POC e regiões de aceitação;
  - filtros para alvo, stop técnico e confluência de preço.
- Limitação:
  - Volume At Price mostra concentração; não prova intenção sozinho.


### B3 — Futuro de Ibovespa / Mini Ibovespa Futures

- Link: https://www.b3.com.br/pt_br/produtos-e-servicos/negociacao/renda-variavel/mercado-de-acoes/futuro-de-ibovespa.htm
- Link em inglês: https://www.b3.com.br/en_us/products-and-services/trading/equities/cash-equities/ibovespa-futures.htm
- Tipo: fonte oficial do produto negociado.
- O que sustenta no projeto:
  - ticker WIN;
  - horário de negociação;
  - tamanho do contrato como pontos do Ibovespa multiplicados por R$ 0,20;
  - variação mínima de 5 pontos;
  - lote mínimo de 1 minicontrato.
- Como influencia o produto:
  - cálculo do alvo mínimo de 500 pontos;
  - cálculo de resultado financeiro;
  - regra de proteção do WIN;
  - parametrização separada de WDO e WIN.
- Limitação:
  - a página define especificações contratuais, mas não valida setups automatizados.

### B3 — Minimum Tick Sizes

- Link: https://www.b3.com.br/data/files/11/73/60/D0/CD3FD910E7DB5DD9AC094EA8/Minimum_Tick_Sizes_EN%20-%2005.04.2026.pdf
- Tipo: fonte oficial de variação mínima.
- O que sustenta no projeto:
  - WDO com tick size 0,5;
  - WIN com tick size 5.
- Como influencia o produto:
  - normalização de alvos e stops;
  - conversão de pontos em ticks;
  - configuração de OCO em ticks.
- Limitação:
  - documento de especificação, não de metodologia operacional.

### Nelogica — Editor de Estratégias / NTSL

- Link: https://ajuda.nelogica.com.br/hc/pt-br/articles/9165042993691-Editor-de-Estrat%C3%A9gias-Crie-estrat%C3%A9gias-pr%C3%B3prias-atrav%C3%A9s-do-Profit
- Tipo: documentação funcional da plataforma.
- O que sustenta no projeto:
  - uso da linguagem NTSL;
  - criação de estratégias de execução;
  - backtest;
  - automação;
  - configuração de slippage e quantidade de contratos;
  - estatísticas do Editor de Estratégias.
- Como influencia o produto:
  - arquitetura de implementação nativa no ProfitPro;
  - definição do que precisa ser confirmado antes de codar;
  - regra de homologação antes de capital real.
- Limitação:
  - a documentação confirma o ambiente, mas cada função e dado necessário deve ser testado na versão alvo do Profit.

### Nelogica — Ordens OCO

- Link: https://ajuda.nelogica.com.br/hc/pt-br/articles/360041299231-Ordens-OCO-Editor-de-Estrat%C3%A9gias-de-Negocia%C3%A7%C3%A3o
- Tipo: documentação funcional da plataforma.
- O que sustenta no projeto:
  - configuração de gain, loss e stop offset;
  - uso de saídas parciais em ticks;
  - comportamento de cancelamento de ordens vinculadas;
  - necessidade de tratar rejeições.
- Como influencia o produto:
  - motor de proteção;
  - regra de break-even/parcial;
  - fallback de zeragem;
  - auditoria de execução.
- Limitação:
  - comportamento real deve ser validado em simulação e ambiente controlado.

## Referências acadêmicas e quantitativas

### Cont, Kukanov e Stoikov — The Price Impact of Order Book Events

- Link: https://academic.oup.com/jfec/article/12/1/47/816163
- DOI: https://doi.org/10.1093/jjfinec/nbt003
- Tipo: artigo acadêmico de microestrutura.
- O que sustenta no projeto:
  - eventos de book como ordens limitadas, ordens a mercado e cancelamentos afetam preço;
  - preço é impactado por uma combinação de eventos, não apenas por trades executados;
  - cancelamentos e mudanças no livro devem ser considerados.
- Como influencia o produto:
  - módulo de Order Book Events;
  - leitura conjunta de agressão, reposição e cancelamento;
  - métricas de impacto pós-evento.
- Limitação:
  - estudo baseado em ações dos EUA; os conceitos precisam ser adaptados e validados no WDO.

### Xu, Gould e Howison — Multi-Level Order-Flow Imbalance

- Link: https://ora.ox.ac.uk/objects/uuid:9b7d0422-4ef1-48e7-a2d4-4eaa8a0a7ec1
- Tipo: pesquisa acadêmica de microestrutura.
- O que sustenta no projeto:
  - Order Flow Imbalance em múltiplos níveis do book pode explicar melhor mudanças de preço do que olhar apenas o melhor bid/ask;
  - profundidade do book deve entrar na leitura quando se busca robustez.
- Como influencia o produto:
  - leitura de desequilíbrio de profundidade;
  - construção de score de pressão compradora/vendedora;
  - análise de book além do topo.
- Limitação:
  - a adaptação para WDO exige dados reais ou simulador calibrado.

## Referências macro e calendário de risco

### Banco Central do Brasil — Copom e calendário

- Link: https://www.bcb.gov.br/controleinflacao/copom
- Link calendário: https://www.bcb.gov.br/acessoinformacao/calendariobc
- Tipo: fonte oficial de política monetária brasileira.
- O que sustenta no projeto:
  - reuniões e decisões do Copom;
  - atas, comunicados e eventos de política monetária;
  - janela de risco para WDO e WIN.
- Como influencia o produto:
  - filtro de notícia;
  - bloqueio de entrada;
  - classificação de regime macro.
- Limitação:
  - informa calendário e conteúdo oficial, mas a reação intraday precisa ser medida por replay e logs.

### Federal Reserve — FOMC calendars

- Link: https://www.federalreserve.gov/monetarypolicy/fomccalendars.htm
- Tipo: fonte oficial de política monetária dos EUA.
- O que sustenta no projeto:
  - datas de reuniões FOMC;
  - comunicados, atas e materiais relacionados;
  - janelas de alto impacto para dólar e índice.
- Como influencia o produto:
  - bloqueios em WDO;
  - redução de prioridade no WIN;
  - auditoria de eventos macro.
- Limitação:
  - não fornece por si só direção operacional; apenas define evento e risco.

### BLS — Economic news release schedules

- Link: https://www.bls.gov/schedule/news_release/
- Tipo: fonte oficial de indicadores econômicos dos EUA.
- O que sustenta no projeto:
  - CPI;
  - payroll/employment situation;
  - PPI e demais divulgações de trabalho/preços.
- Como influencia o produto:
  - calendário de notícia;
  - bloqueios antes/depois de divulgação;
  - pesquisa de eventos anteriores.
- Limitação:
  - calendário não substitui análise de reação real do mercado.

### BEA — Release schedule

- Link: https://www.bea.gov/news/schedule/
- Tipo: fonte oficial de dados econômicos dos EUA.
- O que sustenta no projeto:
  - GDP;
  - PCE;
  - dados de contas nacionais e comércio.
- Como influencia o produto:
  - filtro macro;
  - bloqueio de eventos de alto/médio impacto;
  - pesquisa histórica de volatilidade.
- Limitação:
  - precisa ser cruzada com reação efetiva do WDO/WIN.

### U.S. Census Bureau — Economic Indicator Release Schedule

- Link: https://www.census.gov/economic-indicators/calendar.html
- Tipo: fonte oficial de indicadores econômicos dos EUA.
- O que sustenta no projeto:
  - retail sales;
  - trade;
  - durable goods;
  - indicadores econômicos com potencial de impacto.
- Como influencia o produto:
  - filtro de notícia;
  - classificação de impacto;
  - auditoria de eventos.
- Limitação:
  - a relevância intraday deve ser calibrada por ativo e regime.

## Regras de uso das referências

1. Fonte oficial define especificação; não define setup.
2. Fonte da plataforma define funcionalidade; não define vantagem estatística.
3. Fonte acadêmica define estrutura conceitual; não garante aplicação direta no WDO.
4. Hipótese operacional só entra no produto após teste em replay, backtest, simulação em tempo real e revisão de risco.
5. Nenhuma automação deve enviar ordem sem proteção, invalidação, bloqueios e logs.
