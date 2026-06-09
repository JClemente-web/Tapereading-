# 100 Perguntas de Investigação — Mini Dólar (WDO) no ProfitPro

## Objetivo

Este roteiro define as 100 perguntas que devem orientar a investigação aprofundada para construir a automação profissional de Tape Reading focada **somente em Mini Dólar (WDO)** no ProfitPro/Nelogica.

## Escopo fechado

- Ativo principal e único desta investigação: **WDO / Mini Dólar**.
- Não incluir WIN nesta rodada.
- Não incluir HST/HFT/high-speed trading proprietário nesta rodada.
- Não aceitar resposta sem fonte, data de consulta, caminho de busca, limitação e impacto no projeto.
- Priorizar documentação oficial da **Nelogica/ProfitPro**, B3 e fontes macro oficiais.

## Fontes prioritárias

1. Nelogica / ProfitPro:
   - Plugin Tape Reading;
   - Gráfico Tape Reading / Footprint;
   - Histograma e Saldo de Agressão;
   - Alarmes de Tape Reading;
   - Times & Trades;
   - Volume At Price;
   - Book/DOM/SuperDOM;
   - Rastreamento de Algoritmos;
   - Editor de Estratégias;
   - NTSL;
   - Automação de Estratégias;
   - Ordens OCO.
2. B3:
   - especificação oficial do contrato WDO;
   - tick size;
   - horários;
   - vencimentos;
   - regras de negociação.
3. Fontes macro oficiais:
   - Banco Central do Brasil;
   - IBGE;
   - Federal Reserve;
   - BLS;
   - BEA;
   - Census Bureau.
4. Pesquisa técnica/quantitativa:
   - Order Flow Imbalance;
   - limit order book;
   - price impact;
   - microestrutura;
   - execução e slippage.

## Formato esperado para responder cada pergunta

Cada resposta da investigação deve trazer:

```text
Pergunta nº:
Resposta objetiva:
Fonte usada:
URL:
Data de consulta:
Termo pesquisado:
Por que essa fonte foi escolhida:
Dado extraído:
Limitação da fonte:
Impacto no projeto:
Regra afetada:
Precisa de teste? sim/não
Como testar:
Status: aprovado / rejeitado / hipótese / pendente
```

## 100 perguntas

### A. Contrato WDO, especificação, horário e risco-base

1. Qual é a especificação oficial atual do contrato WDO na B3: tamanho, cotação, tick, lote mínimo, vencimento e código?
2. Qual é o valor oficial por tick e por ponto do WDO, e como isso deve ser convertido em alvo de 4 pontos e meta diária de 8 pontos?
3. Quais são os horários oficiais de negociação do WDO, incluindo abertura, encerramento, after-market, leilões e possíveis alterações por calendário?
4. Quais vencimentos do WDO têm maior liquidez e como a automação deve escolher o contrato ativo correto automaticamente?
5. Quais são as regras oficiais da B3 para ajustes, vencimento, rolagem e último dia de negociação do WDO?
6. Quais condições especiais da B3 podem suspender, limitar ou alterar a negociação do WDO durante o pregão?
7. Existe regra oficial de túnel de negociação, leilão, rejeição ou limite operacional que afete ordens automatizadas no WDO?
8. Qual é o impacto de operar WDO em dias de vencimento, rolagem ou véspera de vencimento, e a automação deve bloquear ou alterar parâmetros nesses dias?
9. Como calcular resultado financeiro real da operação considerando pontos, contratos, corretagem, emolumentos, impostos e custos operacionais?
10. Qual deve ser o limite máximo de perda diária, perda por trade e número máximo de operações para uma estratégia que busca 2 operações de 4 pontos no WDO?

### B. ProfitPro/Nelogica — o que é possível fazer nativamente

11. Quais versões do ProfitPro/Profit Ultra disponibilizam nativamente o Plugin Tape Reading e quais exigem contratação separada?
12. Quais recursos do Plugin Tape Reading existem oficialmente: Footprint, análise de ativos, análise de players, ranking, indicadores de agressão, alarmes e periodicidades?
13. Quais dados do Plugin Tape Reading são apenas visuais e quais podem ser utilizados programaticamente em NTSL ou automação?
14. O ProfitPro permite automatizar decisão baseada diretamente em saldo de agressão, histograma de agressão ou indicadores TR?
15. O ProfitPro permite automatizar decisão baseada diretamente no Footprint ou ele é somente visual?
16. O ProfitPro permite automatizar decisão baseada em Times & Trades, agressor, ordem original, compradores, vendedores ou saldo de players?
17. O ProfitPro permite automatizar decisão baseada no Book/DOM/profundidade, incluindo walls, reposição, remoção e desequilíbrio de níveis?
18. O ProfitPro permite automatizar decisão baseada em Volume At Price, POC, regiões de volume e volume por preço?
19. Quais dados do ProfitPro podem ser exportados para replay, auditoria ou processamento externo?
20. Quais limitações oficiais da Nelogica existem para automação, NTSL, dados de fluxo, book, players e Tape Reading?

### C. NTSL, Editor de Estratégias e execução automatizada

21. Quais funções NTSL existem para enviar compra, venda, ordem limitada, ordem stop, ordem a mercado e zeragem de posição?
22. Quais funções NTSL existem para consultar posição atual, preço médio, quantidade, ordens pendentes e estado da estratégia?
23. Como o Editor de Estratégias configura ativo, quantidade, slippage, replay, backtest, conta e parâmetros da automação?
24. Como a automação no ProfitPro trata rejeição de ordem, falha de roteamento, desconexão, latência ou divergência entre posição real e posição da estratégia?
25. O NTSL permite criar kill switch por perda diária, ganho diário, número de operações, horário, notícia ou falha de dados?
26. Como registrar logs no ProfitPro/NTSL para cada decisão de operar e de não operar?
27. Como fazer backtest no Editor de Estratégias para uma estratégia intraday de WDO buscando 4 pontos?
28. O backtest do ProfitPro reproduz agressão, book e Tape Reading com fidelidade suficiente para validar essa estratégia?
29. Como rodar a estratégia em simulação/conta demo antes de liberar capital real?
30. Quais diferenças documentadas existem entre backtest, replay, simulação e execução real no ProfitPro?

### D. Ordens OCO, stop, gain, proteção e falhas

31. Como configurar OCO no ProfitPro/NTSL com gain de 4 pontos no WDO?
32. Como configurar stop loss em ticks/pontos no WDO e como definir stop offset corretamente?
33. O ProfitPro permite alterar stop automaticamente para break-even após deslocamento favorável no WDO?
34. O ProfitPro permite saída parcial, trailing stop ou proteção dinâmica em NTSL para WDO?
35. Qual deve ser a regra de proteção se o WDO andar a favor, mas não atingir os 4 pontos e o fluxo inverter?
36. Qual deve ser a regra de zeragem se a OCO for rejeitada ou se uma das pernas não for enviada?
37. Como auditar se gain, loss, stop offset e cancelamento de ordens vinculadas funcionaram corretamente?
38. Qual é o slippage médio/aceitável para uma operação de 4 pontos no WDO e como medir isso no ProfitPro?
39. Qual é o stop máximo aceitável para buscar 4 pontos sem tornar a relação risco-retorno inviável?
40. A automação deve parar após atingir 4 pontos uma vez, ou continuar até duas operações/8 pontos somente se o contexto permanecer favorável?

### E. Tape Reading Nelogica — Footprint, agressão e saldo

41. Como a Nelogica define oficialmente agressão de compra e agressão de venda no Tape Reading?
42. Como o Gráfico Tape Reading/Footprint exibe agressões por nível de preço dentro do candle?
43. Como funciona a leitura diagonal do Footprint na documentação da Nelogica?
44. Como configurar e interpretar o Fator de Imbalance no Footprint para WDO?
45. Como configurar e interpretar Fator Sequencial, Exaustão e demais parâmetros visuais do Tape Reading?
46. Como o primeiro retângulo de saldo do candle e o segundo retângulo de saldo diário do Footprint devem ser interpretados?
47. Como o TR - Histograma de Agressão é calculado e como pode ser usado para confirmar dominância de fluxo?
48. Como o TR - Acúmulo de Agressão / Saldo é calculado e qual janela deve ser usada para scalp de 4 pontos?
49. Como o divisor Bid-Ask do gráfico de Tape Reading pode melhorar a leitura do WDO?
50. Quais configurações oficiais ou recomendadas pela Nelogica existem para Tape Reading no WDO, e quais precisam ser calibradas por teste próprio?

### F. Times & Trades, players e ordem original

51. Quais colunas e abas do Times & Trades são oficialmente disponíveis para analisar WDO?
52. Como o Times & Trades identifica agressor, corretora, quantidade, preço, ordem original, compradores, vendedores e saldo?
53. O que a Nelogica diz oficialmente sobre identificação de grandes players no Times & Trades?
54. Como diferenciar player relevante de fluxo pulverizado ou varejo usando saldo, agressão e evolução no tempo?
55. Como medir se um player realmente desloca preço ou se está sendo absorvido?
56. Quais players/corretoras devem ser acompanhados por comportamento no WDO sem assumir que nome sozinho é sinal?
57. Como identificar mudança de lado de um player e transformar isso em redução de confiança ou bloqueio?
58. Como usar ordem original para detectar ordem grande, fatiamento, possível iceberg ou varredura de níveis?
59. Como registrar no log cada evento de player relevante: horário, preço, lado, volume, saldo e impacto?
60. Quais limitações de player existem por ativo, tipo de mercado, RLP, commodity ou dado não repassado pela B3/Nelogica?

### G. Book/DOM, liquidez, wall, spoofing e iceberg

61. Quais ferramentas oficiais do ProfitPro mostram Book, DOM, SuperDOM, profundidade e ofertas no WDO?
62. O ProfitPro/NTSL permite ler book/profundidade programaticamente ou apenas visualmente?
63. Como definir wall relevante no WDO por comparação com níveis vizinhos e liquidez média do dia?
64. Como detectar remoção brusca de liquidez antes de rompimento ou falso rompimento?
65. Como detectar reposição de liquidez após agressão como sinal de absorção?
66. Como classificar spoofing apenas como suspeita, evitando afirmar manipulação sem execução/registro suficiente?
67. Como inferir iceberg no WDO comparando volume executado, liquidez visível e reposição repetida?
68. Como medir desequilíbrio de book em 1, 5 e 10 níveis e decidir se isso melhora a entrada de 4 pontos?
69. Como o book deve bloquear entrada quando existe barreira contrária dentro do alvo de 4 pontos?
70. Como registrar book snapshot antes, durante e depois da entrada para auditoria?

### H. Volume At Price, VWAP, regiões e alvo de 4 pontos

71. Como o Volume At Price do ProfitPro calcula volume por preço no WDO?
72. Como identificar POC, regiões de aceitação, defesa e rejeição usando Volume At Price?
73. O ProfitPro/NTSL permite usar Volume At Price programaticamente em regra de entrada ou apenas visualmente?
74. Como usar VWAP no WDO como filtro de contexto sem transformar VWAP em gatilho isolado?
75. Como saber se existe espaço técnico/volumétrico livre até o alvo de 4 pontos?
76. Como impedir entrada quando o POC, VWAP, máxima/mínima anterior ou região de volume está imediatamente contra o alvo?
77. Quais janelas de Volume At Price devem ser testadas para scalp: dia inteiro, abertura, últimos 5 min, últimos 15 min ou janela dinâmica?
78. Como combinar Volume At Price com Footprint para diferenciar rompimento válido de absorção?
79. Como usar regiões de alto volume para posicionar stop técnico e não apenas stop fixo?
80. Como medir estatisticamente se confluência com VAP/VWAP melhora a taxa de atingir 4 pontos antes do stop?

### I. Notícias, macro, correlações e bloqueios

81. Quais eventos macro brasileiros devem bloquear ou reduzir prioridade no WDO: Copom, ata, Focus, IPCA, PIB, fiscal, política e câmbio?
82. Quais eventos dos EUA devem bloquear ou reduzir prioridade no WDO: FOMC, payroll, CPI, PCE, PPI, GDP, retail sales, claims e falas do Fed?
83. Quais fontes oficiais devem ser usadas para calendário macro e como a automação deve consultar/registrar esses eventos?
84. Qual janela de bloqueio antes/depois de notícia deve ser testada para WDO?
85. Como pesquisar notícias anteriores e medir volatilidade, slippage, spread, direção, falsos rompimentos e comportamento do delta após cada evento?
86. Quais correlações externas realmente importam para WDO: DOL cheio, dólar à vista, DXY, juros dos EUA, S&P/Nasdaq, petróleo, ouro e risco global?
87. Quais dessas correlações estão disponíveis no ProfitPro e quais exigem fonte externa?
88. Como evitar que correlação gere entrada sozinha e usá-la apenas como filtro de contexto/bloqueio?
89. Em quais horários o WDO costuma ter maior qualidade para scalp de 4 pontos e quais horários devem ser bloqueados por ruído/liquidez?
90. A automação deve encerrar ou impedir posição perto do fechamento, ajuste, notícia ou evento de rolagem?

### J. Validação, estatística, auditoria e homologação

91. Qual métrica define sucesso do setup: atingir 4 pontos antes de andar X pontos contra, tempo até alvo, MFE/MAE, slippage e qualidade do fluxo?
92. Quantos eventos/replays são necessários antes de aprovar uma regra de WDO para simulação em tempo real?
93. Como separar resultados por regime: tendência, lateral, notícia, abertura, almoço, final de pregão, fluxo climático e baixa liquidez?
94. Como medir falso positivo de rompimento, absorção, exaustão, wall, player relevante e imbalance?
95. Como comparar regra com e sem determinada confluência para saber se ela melhora ou piora o resultado?
96. Como registrar decisões de não entrada e medir se os bloqueios evitaram trades ruins?
97. Quais relatórios diários a automação deve produzir: operações, bloqueios, alertas, fontes, falhas, slippage, MFE/MAE e aderência às regras?
98. Quais critérios mínimos devem liberar a automação para capital real após backtest, replay e simulação?
99. Qual deve ser o plano de rollback/kill switch se a automação operar fora do esperado?
100. Qual é o checklist final de revisão sênior antes de transformar uma regra pesquisada em código NTSL ativo no ProfitPro?

## Entregável esperado da investigação

Ao final da pesquisa, cada pergunta deve gerar uma das quatro decisões:

1. **Regra implementável**: existe fonte, dado disponível, teste e critério de execução.
2. **Regra visual/manual**: existe no ProfitPro, mas ainda não há confirmação de acesso programático.
3. **Hipótese a testar**: faz sentido operacional, mas precisa de replay/backtest/log.
4. **Rejeitada**: fonte insuficiente, dado indisponível, risco alto ou sem impacto comprovável.

## Ordem recomendada de investigação

1. Perguntas 1 a 10: contrato WDO e risco-base.
2. Perguntas 11 a 20: disponibilidade real no ProfitPro/Nelogica.
3. Perguntas 21 a 40: NTSL, execução e proteção.
4. Perguntas 41 a 60: Tape Reading, Footprint, agressão e players.
5. Perguntas 61 a 80: book, VAP, VWAP e alvo de 4 pontos.
6. Perguntas 81 a 90: notícia, macro e correlações.
7. Perguntas 91 a 100: validação, auditoria e homologação.
