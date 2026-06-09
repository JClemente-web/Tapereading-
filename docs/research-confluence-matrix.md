# Matriz Profissional de Confluências

## Objetivo

Esta matriz transforma conceitos de Tape Reading em sinais verificáveis. Cada sinal precisa ter dados, confluências, invalidação e referência. O objetivo é evitar que a ferramenta gere alertas banais baseados em prints isolados.

## Regras gerais

1. Um sinal só é candidato a alerta quando possui pelo menos duas confluências independentes.
2. Todo sinal deve ter uma condição de invalidação.
3. Todo sinal deve ser registrado para replay.
4. Nenhum sinal isolado pode executar ordem; execução exige regra completa, proteção, bloqueios e auditoria.
5. Sinais devem ser separados por regime de mercado e horário.

## Matriz

| Sinal | Dados necessários | Confluências mínimas | Invalidação | Referências | Observação para WDO |
| --- | --- | --- | --- | --- | --- |
| Compra dominante | Times & Trades, agressor, delta, preço | agressões compradoras relevantes; delta positivo; preço deslocando a favor | compras deixam de deslocar ou surge venda agressora maior | Nelogica Footprint; Histograma de Agressão | útil para scalp curto se houver espaço até próxima liquidez |
| Venda dominante | Times & Trades, agressor, delta, preço | agressões vendedoras relevantes; delta negativo; preço deslocando a favor | vendas deixam de deslocar ou surge compra agressora maior | Nelogica Footprint; Histograma de Agressão | útil para continuação se o book abaixo estiver fino |
| Compra absorvida | agressão compradora, preço, DOM, volume por preço | compra forte; pouco deslocamento; oferta passiva defendendo ou repondo | rompimento com continuidade e pouca reposição contrária | Cont/Kukanov/Stoikov; Nelogica Footprint | pode indicar vendedor institucional defendendo região |
| Venda absorvida | agressão vendedora, preço, DOM, volume por preço | venda forte; pouco deslocamento; compra passiva defendendo ou repondo | rompimento de suporte com continuidade e book sem defesa | Cont/Kukanov/Stoikov; Nelogica Footprint | pode indicar comprador absorvendo pressão no fundo |
| Imbalance agressivo | footprint, delta por preço, agressor | razão compra/venda acima do fator; sequência de agressões; deslocamento | imbalance isolado sem deslocamento ou com absorção contrária | Nelogica Footprint | fator inicial pode ser 2x, mas deve ser calibrado |
| Exaustão compradora | delta, agressão, preço, volume | preço sobe com delta perdendo força; lotes menores; venda surgindo no topo | nova sequência compradora com deslocamento | Histograma de Agressão; Volume At Price | útil para evitar compra tardia buscando apenas 4 pontos |
| Exaustão vendedora | delta, agressão, preço, volume | preço cai com delta perdendo força; lotes menores; compra surgindo no fundo | nova sequência vendedora com deslocamento | Histograma de Agressão; Volume At Price | útil para evitar venda tardia em fundo estendido |
| Rompimento confirmado | preço, agressão, DOM, VAP | agressão no sentido do rompimento; liquidez consumida; delta confirma | preço volta ao nível rompido com fluxo contrário | Nelogica Footprint; Volume At Price | precisa de espaço livre até alvo mínimo do modo operacional |
| Falso rompimento provável | preço, agressão, delta, DOM | rompimento sem continuidade; delta falha; liquidez contrária reaparece | novo fluxo no sentido do rompimento com deslocamento | Order book events; Footprint | importante para não perseguir movimento curto sem confirmação |
| Wall relevante | DOM, profundidade, volume por preço | lote muito acima dos níveis vizinhos; permanência; reação do preço | wall removido sem execução ou consumido com continuidade | Multi-Level OFI; Volume At Price | deve ser tratado como liquidez potencial, não intenção garantida |
| Spoofing suspeito | DOM, cancelamentos, negócios correspondentes | parede grande aparece; preço reage; ordem some sem execução proporcional | ordem é executada ou permanece com defesa real | Order book events | classificar como suspeita, nunca como certeza |
| Iceberg suspeito | negócios no mesmo preço, DOM, ordem original | volume executado excede liquidez visível; reposição repetida; preço travado | liquidez para de repor ou preço rompe com continuidade | Order book events; Times & Trades | inferência probabilística; não é detecção direta |
| Player relevante | Times & Trades, saldo, compradores/vendedores | player com saldo dominante; sequência consistente; impacto no preço | player vira lado ou fluxo perde efeito | Nelogica Times & Trades | player isolado não basta; precisa de comportamento e impacto |
| Fluxo climático | volume, agressão, velocidade, preço | volume anormal; velocidade alta; extensão do movimento | continuidade limpa sem perda de intensidade | Histograma de Agressão | pode ser clímax ou início de tendência; precisa contexto |

## Como usar a matriz no produto

A matriz deve alimentar o Alert Engine. Cada linha vira uma regra candidata. O motor deve calcular:

- presença da confluência;
- ausência da confluência;
- força do sinal;
- condição de invalidação;
- risco de falso positivo;
- compatibilidade com o modo operacional ativo.

## Compatibilidade com o objetivo de 4 pontos

Para o modo Scalp 4 Pontos, o alerta só deve receber alta prioridade quando:

- existe espaço técnico ou volumétrico até pelo menos 4 pontos;
- a invalidação não exige stop desproporcional;
- o fluxo está eficiente;
- o book não mostra barreira contrária imediata;
- o horário não está classificado como ruído elevado.

Caso contrário, o alerta pode aparecer como observação, mas não como oportunidade principal.
