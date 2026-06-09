# Protocolo de Pesquisa, Investigação e Fontes

## Objetivo

Toda investigação do projeto deve ser rastreável. Nenhuma regra operacional deve ser aceita porque “parece fazer sentido”. Cada regra precisa responder de onde veio, como foi pesquisada, por que a fonte foi escolhida, qual dado foi extraído, como será validada e quais limitações existem.

## Classificação das fontes

### Fonte oficial

Usada para especificações, calendário, contrato, regra de mercado e dados primários.

Exemplos:

- B3;
- Banco Central do Brasil;
- Federal Reserve;
- BLS;
- BEA;
- U.S. Census Bureau;
- CME, quando usada para correlação externa;
- comunicados oficiais de órgãos econômicos.

### Fonte funcional

Usada para entender o que o ProfitPro/Nelogica permite fazer.

Exemplos:

- Central de Ajuda Nelogica;
- Manual NTSL;
- documentação do Editor de Estratégias;
- documentação de Automação de Estratégias;
- documentação de OCO, alarmes, Times & Trades, Tape Reading e Volume At Price.

### Fonte acadêmica ou quantitativa

Usada para justificar modelos de microestrutura e impacto de ordens.

Exemplos:

- Order Flow Imbalance;
- Multi-Level Order-Flow Imbalance;
- Price Impact of Order Book Events;
- estudos de limit order book;
- estudos de execução algorítmica e slippage.

### Fonte operacional

Usada apenas como hipótese, nunca como verdade final.

Exemplos:

- observações de mesa;
- replay próprio;
- diário operacional;
- estatísticas da automação;
- comportamento histórico do setup.

## Template obrigatório de investigação

Toda pesquisa deve preencher:

```text
ID da investigação:
Pergunta:
Hipótese:
Ativo:
Fonte consultada:
Tipo da fonte:
URL ou origem:
Data da consulta:
Como foi buscada:
Por que a fonte foi escolhida:
Dado extraído:
Regra impactada:
Módulo impactado:
Limitação da fonte:
Teste necessário:
Critério de aprovação:
Critério de rejeição:
Status:
```

## Perguntas obrigatórias

Cada investigação deve responder:

- **Onde** o dado será usado?
- **Como** o dado será coletado?
- **Por que** esse dado tem valor operacional?
- **Quando** ele é válido?
- **Quando** ele deve ser ignorado?
- **Quais condições são necessárias?**
- **Quais condições bloqueiam a entrada?**
- **Quais confluências aumentam a qualidade?**
- **Qual fonte primária sustenta isso?**
- **Como o resultado será auditado?**

## Pesquisas obrigatórias do projeto

### INV-001 — Especificação WDO

- Fonte primária: B3.
- Objetivo: confirmar ticker, tick, valor por tick, tamanho do contrato, lote mínimo e vencimento.
- Uso: cálculo de alvo, stop, resultado financeiro e gestão de risco.

### INV-002 — Especificação WIN

- Fonte primária: B3.
- Objetivo: confirmar ticker, tick, multiplicador, lote mínimo e horário.
- Uso: cálculo do alvo mínimo de 500 pontos, proteção e resultado financeiro.

### INV-003 — Automação no ProfitPro

- Fonte primária: Nelogica.
- Objetivo: mapear Editor de Estratégias, NTSL, backtest, automação e limitações.
- Uso: decidir o que será implementado nativamente e o que exigirá camada externa.

### INV-004 — OCO, stops e proteção

- Fonte primária: Nelogica.
- Objetivo: mapear gain, loss, stop offset, parciais, rejeições e cancelamento automático.
- Uso: motor de proteção.

### INV-005 — Tape Reading e agressão no ProfitPro

- Fonte primária: Nelogica.
- Objetivo: mapear Footprint, Times & Trades, saldo de agressão, players, alarmes e Volume At Price.
- Uso: motor de confluências.

### INV-006 — Calendário macro Brasil

- Fonte primária: Banco Central do Brasil e demais órgãos oficiais.
- Objetivo: identificar Copom, atas, relatórios, Focus, IPCA e eventos com impacto no câmbio e índice.
- Uso: filtro de notícia e bloqueio operacional.

### INV-007 — Calendário macro EUA

- Fonte primária: Federal Reserve, BLS, BEA e Census.
- Objetivo: identificar FOMC, payroll, CPI, PPI, GDP, retail sales e indicadores de alta relevância.
- Uso: bloqueio de entradas e regime de notícia.

### INV-008 — Correlações externas

- Fontes: ativos de referência e provedores de mercado disponíveis.
- Objetivo: avaliar necessidade de observar DXY, treasury yields, S&P 500, petróleo, ouro e dólar futuro cheio.
- Uso: filtros macro e regime.

### INV-009 — Big players e participantes

- Fonte primária: dados disponíveis no ProfitPro via Times & Trades, saldo, compradores/vendedores e players.
- Objetivo: mapear participantes relevantes por comportamento, não por suposição fixa.
- Uso: score de player relevante.

### INV-010 — Validação estatística dos setups

- Fonte: replay, backtest, logs e simulação em tempo real.
- Objetivo: medir se cada alerta atinge o deslocamento esperado antes da invalidação.
- Uso: aprovação ou rejeição de regras.

## Política de aceitação de informação

Uma informação só pode entrar como regra operacional quando cumprir pelo menos uma das condições:

1. está em fonte oficial;
2. está em documentação funcional da plataforma;
3. está sustentada por pesquisa acadêmica e foi adaptada ao contexto;
4. foi validada por replay/backtest/log próprio;
5. foi aprovada por revisão de risco.

Informação de fórum, opinião, vídeo ou experiência isolada só pode entrar como hipótese a testar.

## Registro de busca

Cada documento derivado de pesquisa deve incluir:

- termos pesquisados;
- fontes abertas;
- fontes rejeitadas;
- motivo da rejeição;
- data da consulta;
- impacto no produto.

## Critério de revisão sênior

Uma investigação é reprovada se:

- não tiver fonte;
- não explicar por que a fonte foi escolhida;
- transformar hipótese em regra;
- não tiver critério de invalidação;
- não tiver plano de teste;
- não separar WDO de WIN;
- não considerar notícia, horário, liquidez e risco.
