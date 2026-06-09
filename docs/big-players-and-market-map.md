# Big Players, Participantes e Mapa de Mercado

## Objetivo

Definir como a ferramenta deve observar participantes relevantes sem transformar nomes de corretoras em crença operacional. O foco é comportamento, saldo, agressão, impacto no preço e recorrência.

## Princípio

Um player relevante não é definido apenas pelo nome. Ele é definido por comportamento mensurável:

- volume acima da média;
- saldo consistente;
- agressão em sequência;
- defesa de preço;
- impacto no deslocamento;
- repetição em regiões importantes;
- atuação em horários críticos;
- relação com notícia ou vencimento.

## Dados necessários

- Times & Trades;
- compradores;
- vendedores;
- saldo por participante;
- ordem original;
- agressão líquida;
- evolução no tempo;
- Volume At Price por participante, se disponível;
- book/DOM por agente, se disponível.

## Participantes a mapear por comportamento

Categorias:

- bancos locais;
- bancos estrangeiros;
- corretoras com fluxo institucional;
- corretoras com fluxo de varejo relevante;
- HFT/market makers;
- hedgers;
- fundos;
- players associados a rolagem/vencimento;
- RLP ou fluxo internalizado, quando aplicável.

## Score de player relevante

O score deve considerar:

```text
score_player = volume_relativo
             + saldo_consistente
             + agressao_sequencial
             + impacto_no_preco
             + permanencia_no_lado
             + atuação_em_região_relevante
             - ruído_de_micro_lotes
             - reversão_frequente_de_lado
```

## Regras de uso

### Pode aumentar confiança quando

- player aparece com saldo crescente no lado do setup;
- agressão do player desloca preço;
- atuação ocorre em região técnica/volumétrica relevante;
- atuação acompanha outros dados de fluxo.

### Deve reduzir confiança quando

- player troca de lado rapidamente;
- volume não desloca preço;
- atuação é isolada;
- há absorção contra o player;
- há notícia ou evento distorcendo o fluxo.

### Deve bloquear inferência quando

- dados de player estão indisponíveis;
- identificação não é confiável;
- há divergência entre saldo e preço;
- o mercado está em condição extrema.

## Big players e WDO

No WDO, a ferramenta deve priorizar:

- bancos e corretoras com saldo relevante;
- participantes que aparecem em agressão sequencial;
- players que defendem regiões repetidamente;
- players que atuam em horários de maior liquidez;
- players que aparecem próximos a notícia ou vencimento.

## Big players e WIN

No WIN, a ferramenta deve priorizar:

- fluxo direcional associado a rompimentos;
- atuação em regiões de VWAP/POC;
- comportamento de players em conjunto com ações líderes;
- confirmação ou divergência com WDO.

## Auditoria de player

Cada evento de player relevante deve registrar:

```text
Player/corretora:
Ativo:
Horário:
Preço:
Lado:
Volume:
Saldo anterior:
Saldo posterior:
Agressão:
Região:
Impacto no preço:
Confluências:
Resultado após 5s/10s/30s/60s:
```

## Proibição operacional

A automação não deve entrar apenas porque um player apareceu. Player é confluência, não gatilho suficiente.
