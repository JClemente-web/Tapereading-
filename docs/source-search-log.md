# Log de Busca de Fontes

## Objetivo

Registrar como as fontes iniciais foram buscadas, por que foram escolhidas e como impactam o projeto. Este arquivo deve ser atualizado a cada nova investigação.

## Critério de escolha

Foram priorizadas fontes oficiais e funcionais:

1. B3 para especificações de WDO e WIN.
2. Nelogica para ProfitPro, NTSL, Editor de Estratégias, automação e OCO.
3. Órgãos oficiais para calendário macro.
4. Pesquisa acadêmica para microestrutura e impacto de ordens.

Fontes comerciais, fóruns, vídeos e opiniões não foram usadas como base de regra operacional. Elas só podem gerar hipóteses a testar.

## Buscas realizadas

| ID | Termo pesquisado | Fonte escolhida | Por que foi escolhida | Dado extraído | Impacto no projeto |
| --- | --- | --- | --- | --- | --- |
| SRC-001 | `B3 Mini U.S. Dollar Futures WDO contract size tick size official` | B3 Mini U.S. Dollar Futures | fonte oficial do contrato | ticker WDO, contrato USD 10.000, cotação BRL/USD 1.000, tick 0,5, lote 1 | cálculo de pontos, ticks, alvo e risco WDO |
| SRC-002 | `B3 Mini Ibovespa Futures WIN contract multiplier tick size official` | B3 Ibovespa Futures | fonte oficial do contrato | ticker WIN, multiplicador R$0,20/ponto, tick 5, horário, lote 1 | regra de alvo mínimo 500 pontos e proteção WIN |
| SRC-003 | `B3 Minimum Tick Sizes WDO WIN 2026` | B3 Minimum Tick Sizes | documento oficial de variação mínima | WDO 0,5 e WIN 5 | validação cruzada dos ticks oficiais |
| SRC-004 | `Nelogica Profit Pro automação estratégias NTSL editor estratégias documentação oficial` | Nelogica Editor de Estratégias | documentação funcional oficial da plataforma | NTSL, tipos de estratégia, backtest, automação, slippage, contratos e estatísticas | arquitetura de implementação ProfitPro/NTSL |
| SRC-005 | `Nelogica Profit Pro roteamento stop loss stop gain OCO documentação oficial` | Nelogica Ordens OCO | documentação funcional oficial da plataforma | gain/loss em ticks, stop offset, parciais, cancelamento e rejeições | motor de proteção e saída |
| SRC-006 | `Nelogica Profit Plugin Tape Reading alarmes agressão footprint` | Nelogica Plugin Tape Reading / Footprint / Alarmes | documentação funcional oficial do módulo de fluxo | agressão, Footprint, alarmes, saldo, players | motor de confluências e alertas |
| SRC-007 | `Federal Reserve FOMC calendars official 2026` | Federal Reserve | fonte primária de política monetária dos EUA | calendário FOMC e comunicados | filtro de notícia WDO/WIN |
| SRC-008 | `Bureau of Labor Statistics economic news release schedule official CPI employment` | BLS | fonte primária de CPI, payroll e trabalho | agenda de indicadores de alto impacto | bloqueio macro e pesquisa de eventos anteriores |
| SRC-009 | `BEA release schedule GDP PCE official` | BEA | fonte primária de GDP/PCE | calendário de divulgações macro | bloqueio macro WDO/WIN |
| SRC-010 | `Cont Kukanov Stoikov The Price Impact of Order Book Events order book events` | Journal of Financial Econometrics | referência acadêmica de microestrutura | impacto de ordens a mercado, limitadas e cancelamentos | leitura conjunta de agressão, book, reposição e cancelamento |
| SRC-011 | `Multi-Level Order-Flow Imbalance limit order book` | Oxford / pesquisa acadêmica | referência acadêmica de OFI multi-nível | importância de múltiplos níveis do book | score de pressão e leitura multi-nível |

## Fontes rejeitadas para regra operacional

| Tipo | Motivo |
| --- | --- |
| Fóruns | não são fonte primária e misturam opinião com experiência individual |
| Vídeos | difíceis de auditar e podem não trazer documentação rastreável |
| Sites comerciais de cursos | conflito de interesse e baixa verificabilidade |
| Notícias sem fonte primária | podem ser usadas para contexto, mas não para regra permanente |
| Experiência isolada | só entra como hipótese operacional a testar |

## Próximas buscas obrigatórias

- Manual NTSL atualizado e funções específicas de ordem, posição, cancelamento e múltiplos ativos.
- Documentação Nelogica de Automação de Estratégias.
- Documentação Nelogica de Estratégias de Múltiplos Ativos.
- Documentação Nelogica de Times & Trades, Tape Reading, Histograma de Agressão e Volume At Price com foco em acesso programático.
- Calendário oficial do Copom e fontes oficiais brasileiras para IPCA, Focus e eventos macro.
- Fontes oficiais de DXY, Treasury yields, S&P/Nasdaq futuros, petróleo e ouro para correlação.

## Padrão de atualização

A cada nova pesquisa, registrar:

```text
Data:
Responsável:
Termo pesquisado:
Fonte aberta:
Fonte escolhida:
Fonte rejeitada:
Motivo da escolha:
Motivo da rejeição:
Dado extraído:
Regra afetada:
Status:
```
