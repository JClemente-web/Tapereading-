# Filtro de Notícias, Macro e Correlações

## Objetivo

A automação deve saber quando operar, quando reduzir prioridade e quando bloquear completamente. WDO e WIN são sensíveis a eventos macro, fluxos externos, juros, câmbio, bolsa americana, commodities e notícias locais.

## Política geral

Notícia de alto impacto não é apenas contexto. É uma condição de risco. A automação deve consultar calendário, classificar impacto, aplicar janela de bloqueio e registrar a decisão.

## Fontes primárias de calendário

### Brasil

- Banco Central do Brasil: Copom, atas, comunicados, Relatório de Inflação e Focus.
- IBGE: IPCA, PIB, desemprego e indicadores nacionais.
- B3: calendário de vencimentos, horários e características de negociação.

### Estados Unidos

- Federal Reserve: calendário FOMC, decisões, atas e comunicados.
- BLS: CPI, PPI, payroll, unemployment, earnings e outros indicadores de trabalho/preços.
- BEA: GDP, PCE e dados de contas nacionais.
- Census Bureau: retail sales, trade, durable goods e indicadores econômicos.

### Fontes agregadoras

Fontes como calendários econômicos agregados podem ser usadas para alerta operacional, mas a validação deve priorizar fonte primária quando houver divergência.

## Classificação de impacto

### Alto impacto

- decisão do FOMC;
- payroll;
- CPI dos EUA;
- PCE dos EUA;
- decisão do Copom;
- IPCA;
- fala ou comunicado inesperado de autoridade monetária;
- evento geopolítico com impacto direto em dólar, juros ou commodities;
- vencimento ou rolagem relevante.

### Médio impacto

- PPI;
- retail sales;
- GDP preliminar/revisado;
- claims;
- dados fiscais relevantes;
- PMI/ISM;
- estoques de petróleo quando o mercado estiver sensível a commodities.

### Baixo impacto

- indicadores secundários sem reação histórica relevante;
- eventos fora da janela de liquidez brasileira;
- dados já amplamente precificados.

## Janelas de bloqueio

Parâmetros iniciais, sujeitos a validação:

- alto impacto: bloquear novas entradas de 5 a 15 minutos antes e 5 a 30 minutos depois;
- médio impacto: reduzir prioridade ou bloquear de 2 a 5 minutos antes e depois;
- baixo impacto: apenas registrar contexto, salvo se volatilidade aumentar.

A janela real deve ser parametrizável por ativo, horário, tipo de notícia e volatilidade do dia.

## Comportamento em notícia

Durante janela de alto impacto:

- não abrir nova posição por padrão;
- proteger posição aberta;
- reduzir tolerância a slippage;
- priorizar zeragem se proteção falhar;
- suspender leitura de Tape Reading se o book estiver instável;
- registrar evento macro no log.

## Pesquisa de notícias anteriores

A ferramenta deve manter histórico de eventos e resultados:

- data;
- evento;
- ativo;
- volatilidade antes;
- volatilidade depois;
- deslocamento máximo;
- slippage observado;
- spreads;
- comportamento do delta;
- setups bloqueados;
- setups permitidos;
- resultado estatístico.

Esse histórico serve para responder se vale a pena operar em determinado tipo de notícia ou se a regra deve bloquear.

## Correlações e instrumentos de contexto

### Para WDO

Candidatos a monitoramento:

- DOL cheio;
- dólar à vista/PTAX, quando disponível;
- DXY;
- treasury yields dos EUA;
- Fed Funds expectations, quando disponível;
- S&P 500/Nasdaq futuros;
- petróleo;
- ouro;
- fluxo de risco global;
- notícias de Brasil, EUA e commodities.

### Para WIN

Candidatos a monitoramento:

- IBOV/IND;
- ações de maior peso no índice;
- S&P 500/Nasdaq futuros;
- WDO/DOL como proxy de pressão cambial;
- juros locais;
- commodities relevantes;
- notícias corporativas e macro.

## Uso das correlações

Correlação não deve gerar entrada sozinha. Ela deve classificar contexto:

- confirma direção;
- contradiz direção;
- aumenta risco;
- reduz prioridade;
- bloqueia operação.

## Regras de não carregamento

A estratégia base não deve carregar posição para o dia seguinte.

Exceções só podem existir se houver:

- regra própria separada;
- margem calculada;
- risco overnight documentado;
- fonte macro validada;
- aprovação explícita no plano de risco.

Para o escopo atual, o padrão é zerar operações intraday.

## Auditoria do filtro macro

Cada bloqueio por notícia deve registrar:

```text
Evento:
Fonte:
Horário previsto:
Ativo afetado:
Impacto:
Janela de bloqueio:
Decisão:
Operação bloqueada:
Motivo:
Resultado do mercado após o evento:
```
