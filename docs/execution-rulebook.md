# Rulebook de Entrada, Saída e Proteção

## Objetivo

Este rulebook define a lógica operacional que a automação deve seguir. O foco é criar regras fiscalizáveis, programáveis e auditáveis para WDO e WIN.

## Estados da automação

### 1. Desligada

Nenhum dado é avaliado e nenhuma ordem pode ser enviada.

### 2. Inicializando

O sistema valida conexão, ativo, horário, parâmetros, limite de risco e disponibilidade de dados.

### 3. Observando

O sistema está lendo mercado, mas ainda não há confluência suficiente.

### 4. Armado

O setup possui confluências suficientes. A automação aguarda gatilho exato.

### 5. Posicionado

Existe posição aberta. O foco deixa de ser entrada e passa a ser proteção.

### 6. Protegendo

O sistema ajusta stop, parcial, trailing, break-even ou zeragem conforme regra.

### 7. Bloqueado

O sistema não pode abrir novas posições até que o motivo de bloqueio seja removido ou até o próximo pregão.

## Regras globais de entrada

A entrada só é permitida se todas as condições globais forem verdadeiras:

1. ativo autorizado;
2. horário autorizado;
3. calendário de notícia não bloqueante;
4. limite de perda diária não atingido;
5. limite de ganho diário não atingido;
6. limite de trades não atingido;
7. dados necessários disponíveis;
8. slippage estimado dentro do limite;
9. regime de mercado classificado;
10. regra de entrada em estado armado;
11. ordem OCO/proteção configurada antes ou imediatamente após a execução;
12. não existir posição conflitante no mesmo ativo.

## Rulebook WDO — Scalp 4 Pontos

### Objetivo

Capturar movimentos curtos de 4 pontos por operação, com limite planejado de duas operações válidas por dia.

### Entrada comprada — WDO

Condições obrigatórias:

1. regime permite scalp comprador;
2. preço acima de região de aceitação ou rompendo resistência com fluxo;
3. agressão compradora relevante;
4. delta de janela curta positivo;
5. fluxo eficiente ou venda absorvida;
6. book sem wall vendedor imediato dentro do alvo de 4 pontos;
7. Volume At Price não mostra POC/resistência imediatamente contra;
8. notícia de alto impacto fora da janela de bloqueio;
9. stop técnico não maior que o risco máximo configurado;
10. motor em estado armado.

Gatilhos possíveis:

- rompimento com agressão compradora e consumo do ask;
- pullback com retomada de compra;
- venda absorvida em suporte com virada de agressão;
- falso rompimento de baixa com retorno e compra dominante.

Invalidação:

- delta vira contra com intensidade;
- agressão compradora deixa de deslocar preço;
- wall vendedor aparece ou reaparece contra o alvo;
- preço perde a região de defesa;
- fluxo contrário rompe a estrutura.

Saída:

- gain de 4 pontos;
- stop técnico;
- stop por fluxo contrário;
- zeragem por notícia;
- zeragem por perda de eficiência;
- proteção se o preço andar a favor e falhar antes do alvo.

### Entrada vendida — WDO

Condições obrigatórias:

1. regime permite scalp vendedor;
2. preço abaixo de região de aceitação ou rompendo suporte com fluxo;
3. agressão vendedora relevante;
4. delta de janela curta negativo;
5. fluxo eficiente ou compra absorvida;
6. book sem wall comprador imediato dentro do alvo de 4 pontos;
7. Volume At Price não mostra POC/suporte imediatamente contra;
8. notícia de alto impacto fora da janela de bloqueio;
9. stop técnico não maior que o risco máximo configurado;
10. motor em estado armado.

Gatilhos possíveis:

- rompimento com agressão vendedora e consumo do bid;
- pullback com retomada de venda;
- compra absorvida em resistência com virada de agressão;
- falso rompimento de alta com retorno e venda dominante.

Invalidação:

- delta vira contra com intensidade;
- agressão vendedora deixa de deslocar preço;
- wall comprador aparece ou reaparece contra o alvo;
- preço recupera a região perdida;
- fluxo contrário rompe a estrutura.

Saída:

- gain de 4 pontos;
- stop técnico;
- stop por fluxo contrário;
- zeragem por notícia;
- zeragem por perda de eficiência;
- proteção se o preço andar a favor e falhar antes do alvo.

## Rulebook WIN — Movimento mínimo 500 pontos

### Objetivo

Capturar movimentos de no mínimo 500 pontos e proteger a posição após deslocamento favorável.

### Entrada comprada — WIN

Condições obrigatórias:

1. regime de alta ou rompimento confirmado;
2. fluxo comprador consistente;
3. correlação com contexto do índice e ativos líderes;
4. ausência de notícia bloqueante;
5. volatilidade compatível com alvo de 500 pontos;
6. espaço técnico até o alvo;
7. stop técnico proporcional;
8. liquidez suficiente.

Confirmações desejadas:

- rompimento de região relevante;
- pullback com defesa;
- VWAP favorável;
- saldo de agressão positivo;
- mini dólar não gerando pressão macro contrária extrema, quando aplicável.

Proteção:

- após deslocamento favorável relevante, mover stop para reduzir risco;
- proteger parte do movimento quando atingir o limite mínimo definido;
- encerrar se fluxo vendedor inverter o regime;
- não carregar posição para o dia seguinte por padrão.

### Entrada vendida — WIN

Condições obrigatórias:

1. regime de baixa ou rompimento confirmado;
2. fluxo vendedor consistente;
3. correlação com contexto do índice e ativos líderes;
4. ausência de notícia bloqueante;
5. volatilidade compatível com alvo de 500 pontos;
6. espaço técnico até o alvo;
7. stop técnico proporcional;
8. liquidez suficiente.

Confirmações desejadas:

- rompimento de suporte relevante;
- pullback com rejeição;
- VWAP desfavorável;
- saldo de agressão negativo;
- mini dólar não gerando distorção que invalide o cenário.

Proteção:

- após deslocamento favorável relevante, mover stop para reduzir risco;
- proteger parte do movimento quando atingir o limite mínimo definido;
- encerrar se fluxo comprador inverter o regime;
- não carregar posição para o dia seguinte por padrão.

## Regras de não entrada

A automação não deve entrar quando:

- faltar dado essencial;
- houver notícia relevante em janela de bloqueio;
- o alvo estiver bloqueado por liquidez contrária;
- o stop técnico for maior que o alvo planejado;
- o sinal for baseado em print isolado;
- o regime estiver lateral e estreito;
- houver spread ou slippage anormal;
- o book estiver instável demais para leitura;
- já houver meta ou perda diária atingida;
- houver divergência crítica entre preço, delta e fluxo;
- existir falha de conexão, roteamento ou dados.

## Regras de saída imediata

A posição deve ser encerrada ou protegida de forma agressiva quando:

- a confluência original desaparece;
- surge fluxo contrário dominante;
- o preço atinge a invalidação;
- há rejeição de OCO ou proteção;
- há notícia inesperada de alto impacto;
- o ativo entra em condição especial;
- o horário limite é atingido;
- o sistema detecta inconsistência operacional.

## Regras de limite diário

Parâmetros iniciais a definir por configuração:

- número máximo de operações por ativo;
- perda máxima diária;
- ganho diário de parada;
- limite de trades consecutivos perdedores;
- cooldown após perda;
- cooldown após ganho;
- bloqueio após slippage anormal;
- bloqueio após rejeição de ordem.

## Padrão de auditoria de cada operação

Toda operação precisa registrar:

```text
Ativo:
Direção:
Setup:
Regime:
Confluências:
Gatilho:
Entrada:
Alvo:
Stop:
Proteção:
Motivo da entrada:
Motivo da saída:
Resultado em pontos:
Resultado financeiro:
Avanço favorável máximo:
Avanço contrário máximo:
Fontes consultadas:
Falhas ou rejeições:
```
