# Tape Reading em Mini Dólar (WDO)

## 1. Fundamentos

Tape Reading é a leitura do fluxo de ordens executadas em tempo real. Em vez de depender apenas de candles históricos, o trader observa negócios, agressões, volume por preço, livro de ofertas e comportamento dos players para entender a pressão compradora ou vendedora no momento atual.

A origem do conceito vem da leitura das antigas fitas de negociação, nas quais cada negócio executado era registrado em sequência. No ambiente moderno, essa fita foi substituída por janelas digitais como Times & Trades, DOM, Book de Ofertas, Volume At Price e gráficos do tipo Footprint.

## 2. Tape Reading tradicional vs. moderno

No modelo tradicional, o trader interpretava a sequência de negócios impressa em fita. No modelo moderno, a essência permanece a mesma, mas as plataformas adicionam recursos como filtros por lote, identificação de agressor, rankings de players, histogramas de saldo, footprints, imbalances e alertas configuráveis.

A principal diferença é que a leitura moderna permite reduzir ruído, destacar eventos relevantes e cruzar execução, liquidez e contexto técnico em tempo real.

## 3. Relação com Order Flow

Tape Reading faz parte da análise de fluxo de ordens. O foco principal está nas ordens executadas, ou seja, nos negócios efetivamente realizados. Já a análise de Order Flow em sentido amplo também pode incluir ordens passivas, profundidade do book, spoofing, icebergs, algoritmos e zonas de liquidez.

Na prática operacional, Tape Reading cruza três dimensões:

1. negócios executados;
2. liquidez passiva no book;
3. efeito da agressão sobre o preço.

## 4. Componentes principais

### Times & Trades

Mostra cada negociação executada, geralmente com horário, preço, quantidade, corretora/player e lado agressor. É a base da leitura do tape.

### Livro de Ofertas / DOM

Mostra as ordens passivas disponíveis nos níveis de compra e venda. Ajuda a identificar liquidez, paredes, reposição, remoção de ordens e possíveis armadilhas.

### Agressão

Agressão é o lado que toma a iniciativa usando ordem a mercado. Compra agressora consome liquidez no ask. Venda agressora consome liquidez no bid.

### Lotes relevantes

Nem todo negócio tem a mesma importância. Trades muito pequenos podem ser ruído. Blocos maiores e sequências consistentes tendem a ser mais informativos.

### Indicadores derivados

Incluem delta, saldo de agressão, imbalance, sequencial, exaustão, volume por preço e padrões de absorção.

## 5. Por que WDO é adequado para Tape Reading

O Mini Dólar tende a ser adequado para Tape Reading por combinar liquidez, volatilidade, tick pequeno, alta frequência de negociação e forte participação de bancos, fundos, hedgers, players estrangeiros, robôs e traders de varejo.

Essa combinação permite observar padrões de agressão, defesa de preço, absorção, rompimento e exaustão com maior riqueza de detalhes.

## 6. Players relevantes

No WDO, a leitura profissional busca identificar a atuação de:

- bancos;
- corretoras de grande porte;
- fundos;
- hedge funds;
- importadores e exportadores;
- players estrangeiros;
- robôs institucionais;
- formadores e provedores de liquidez.

A identificação deve ser feita pelo comportamento agregado, não por um print isolado.

## 7. Tape Reading vs. Price Action

Price Action mostra o resultado visual da movimentação do preço. Tape Reading mostra parte do processo interno que levou a esse resultado.

Um rompimento no gráfico pode ser verdadeiro ou falso. O Tape Reading ajuda a avaliar se houve agressão suficiente, se a liquidez foi consumida, se houve absorção ou se o movimento não teve continuidade.

## 8. Conceitos operacionais essenciais

### Agressor vs. passivo

O agressor toma liquidez. O passivo fornece liquidez. Essa distinção é essencial para entender pressão, defesa e absorção.

### Absorção

Absorção ocorre quando há forte agressão de um lado, mas o preço não se desloca proporcionalmente. Isso indica que o lado oposto está aceitando ou defendendo aquele fluxo.

Exemplo: muitas compras agressoras entram em uma resistência, mas o preço não rompe. Isso pode indicar vendedor passivo absorvendo a compra.

### Imbalance

Imbalance é o desequilíbrio entre compra e venda em determinado candle, preço ou janela de tempo. Um exemplo simples seria volume comprador três vezes maior que o volume vendedor no mesmo contexto.

### Exaustão

Exaustão ocorre quando o lado dominante perde intensidade. Pode aparecer como queda no tamanho dos lotes, delta divergente, menor deslocamento do preço ou surgimento de agressão contrária.

### Fluxo climático

Fluxo climático é um pico anormal de agressão e volume, geralmente associado a capitulação, encerramento de movimento ou possível reversão/pausa.

### Wall

Wall é uma concentração grande de ordens passivas em um nível do book. Pode atuar como suporte, resistência, atração de preço ou armadilha.

### Spoofing

Spoofing é a inserção de grandes ordens sem intenção real de execução, buscando induzir leitura falsa de liquidez. A suspeita surge quando uma parede aparece e desaparece rapidamente sem negócios correspondentes.

### Iceberg

Iceberg é uma ordem grande fatiada, em que apenas parte aparece no book. Pode ser inferido quando um preço continua executando volume relevante sem que a quantidade visível explique todo o volume negociado.

### Trapping

Trapping ocorre quando traders entram em um movimento aparentemente confirmado, mas o fluxo rapidamente se inverte e prende compradores ou vendedores no lado errado.

## 9. Ferramentas do ProfitPro relevantes

### Times & Trades

Usado para acompanhar negócios, agressor, quantidade, players, ordem original, compradores, vendedores e saldo.

### DOM / Book de Ofertas

Usado para observar liquidez passiva, profundidade, paredes, reposição, consumo e remoção de ordens.

### Footprint / Gráfico Tape Reading

Usado para visualizar agressão compradora e vendedora por preço dentro dos candles.

### Volume At Price

Usado para identificar volume negociado por nível de preço, POC, zonas de defesa, regiões de aceitação e possíveis áreas de liquidez.

### Saldo de agressão / Delta

Usado para comparar volume comprador e vendedor, avaliar dominância de fluxo e identificar divergências.

### Alertas

Podem ser configurados para eventos como ordem original acima de determinado lote, presença de player, inversão de fluxo, sequencial, imbalance, exaustão e saldo acumulado.

## 10. Configurações sugeridas para WDO

As faixas exatas devem ser ajustadas à liquidez do dia, mas uma referência inicial para leitura pode ser:

- 1 a 4 contratos: micro fluxo / ruído;
- 5 a 10 contratos: fluxo pequeno;
- 50 contratos: fluxo relevante;
- 100 contratos: bloco médio relevante;
- 500 contratos: bloco grande;
- 1000 ou mais contratos: evento extraordinário.

Filtros recomendados:

- ocultar ou reduzir destaque de negócios muito pequenos;
- destacar lotes grandes;
- separar janelas para fluxo bruto e fluxo filtrado;
- usar DOM com profundidade suficiente para enxergar liquidez próxima;
- configurar alertas sonoros apenas para eventos realmente relevantes.

## 11. Setups práticos

### Suporte/resistência com confirmação de fluxo

1. Identificar nível técnico relevante.
2. Observar chegada do preço ao nível.
3. Confirmar defesa, absorção ou agressão dominante.
4. Entrar apenas após confirmação de fluxo.
5. Posicionar stop onde a leitura é invalidada.

### Pullback com retomada de fluxo

1. Identificar tendência principal.
2. Esperar correção contra a tendência.
3. Observar redução da agressão contrária.
4. Entrar quando o lado da tendência volta a agredir.

### Breakout confirmado

1. Identificar resistência ou suporte.
2. Esperar rompimento com agressão forte.
3. Confirmar consumo de liquidez no book.
4. Evitar entrada se o rompimento ocorrer sem volume ou com absorção contrária.

### Reversão por fluxo

1. Observar movimento estendido.
2. Procurar exaustão do lado dominante.
3. Confirmar agressão contrária e possível absorção.
4. Entrar somente após sinal de inversão do fluxo.

## 12. Gestão de risco

Tape Reading não elimina risco. O stop deve ficar onde a leitura de fluxo deixa de fazer sentido. O alvo pode ser definido por:

- próxima região de liquidez;
- resistência ou suporte anterior;
- POC ou área de volume relevante;
- perda de momentum;
- inversão do delta;
- relação risco-retorno previamente definida.

A ferramenta deve reforçar disciplina, não incentivar overtrading.

## 13. Erros comuns

- Operar prints isolados sem contexto.
- Não filtrar ruído.
- Confundir ordem grande no book com intenção real.
- Ignorar notícias e horários de alta volatilidade.
- Entrar em rompimento sem confirmação de agressão.
- Permanecer na operação quando o fluxo invalida a tese.
- Usar Tape Reading como previsão infalível em vez de leitura probabilística.

## 14. Uso em automação profissional

Os conceitos aqui descritos são insumos para regras automatizadas, mas só podem virar execução real quando forem convertidos em critérios objetivos, testados em backtest/replay, validados em simulação, protegidos por OCO/stop e auditados por logs. Tape Reading é leitura de microestrutura em tempo real; a automação deve tratar cada sinal como hipótese operacional sujeita a invalidação.
