# Plano Sênior de Execução

## Resposta direta: o que fazer agora

O próximo passo não é pedir apenas “mais um documento de pesquisa”. O próximo passo é montar uma estrutura profissional em três trilhas paralelas:

1. **Pesquisa rastreável**: referências oficiais, funcionais e acadêmicas para sustentar cada decisão.
2. **Modelo operacional**: transformar Tape Reading em sinais, confluências, invalidações e métricas.
3. **Automação validável**: especificar, testar e auditar a execução no ProfitPro/NTSL antes de liberar capital real.

A documentação inicial criou a base. Agora precisamos criar a arquitetura de decisão do produto.

## Seu objetivo operacional de 8 pontos

Você citou buscar 8 pontos no dia, em duas entradas de 4 pontos cada. No WDO, pela especificação contratual da B3, o contrato tem tamanho de USD 10.000, cotação em BRL por USD 1.000 e tick size de 0,5 ponto. Isso implica:

- 1 tick = 0,5 ponto;
- 1 tick = R$ 5,00 por contrato;
- 1 ponto = R$ 10,00 por contrato;
- 4 pontos = R$ 40,00 por contrato;
- 8 pontos = R$ 80,00 por contrato.

Essa informação deve entrar no produto como **métrica de planejamento e risco**, não como promessa de resultado. A ferramenta deve ajudar a responder: “o contexto atual justifica procurar um scalp de 4 pontos ou o fluxo está poluído demais?”.

## Mentalidade profissional

Uma mesa profissional não pergunta apenas “devo comprar ou vender?”. Ela pergunta:

- qual é o regime do mercado agora?
- existe liquidez suficiente para executar e sair?
- o fluxo confirma o preço?
- existe absorção ou deslocamento real?
- qual é a assimetria em ticks?
- onde a tese é invalidada?
- quantas vezes esse padrão funcionou em contexto parecido?
- o horário atual aumenta ou reduz a confiabilidade do sinal?

Portanto, o projeto precisa nascer como uma ferramenta de **classificação de contexto**, não como um gerador banal de sinais.

## O que não pode faltar no projeto

### 1. Regime de mercado

Antes de qualquer alerta, a ferramenta deve classificar o ambiente:

- tendência de alta;
- tendência de baixa;
- lateralidade;
- abertura volátil;
- notícia/macro;
- baixa liquidez;
- horário de almoço;
- aproximação de ajuste;
- consolidação pré-rompimento;
- fluxo climático.

Sem regime, o mesmo sinal pode ter significado oposto.

### 2. Confluência mínima

Nenhum sinal deve disparar apenas por um fator. Exemplo profissional de absorção:

- agressão relevante;
- pouco deslocamento de preço;
- defesa ou reposição no book;
- região técnica ou volumétrica relevante;
- delta perdendo eficiência;
- invalidação clara.

### 3. Métrica de eficiência do fluxo

O produto deve medir se a agressão está produzindo deslocamento.

Exemplo:

```text
Eficiência = deslocamento_em_ticks / volume_agressor_relevante
```

Se entra muito volume comprador e o preço não sobe, o sistema deve suspeitar de absorção. Se entra volume comprador e o preço desloca com baixa resistência, o sistema deve classificar como fluxo eficiente.

### 4. Score de contexto

Em vez de “compra” ou “venda”, o sistema deve gerar scores:

- score comprador;
- score vendedor;
- score de absorção;
- score de exaustão;
- score de rompimento;
- score de armadilha;
- score de ruído.

Isso torna a ferramenta menos banal e mais próxima de uma mesa profissional.

### 5. Alerta com invalidação

Todo alerta precisa vir com:

- motivo;
- confluências presentes;
- confluências ausentes;
- preço ou condição de invalidação;
- risco de falso positivo;
- janela de tempo esperada.

Um alerta sem invalidação é apenas ruído colorido.

### 6. Replay e auditoria

Para ser profissional, o produto precisa registrar cada alerta e permitir estudo posterior.

Campos mínimos:

- horário;
- preço;
- tipo de alerta;
- score;
- delta antes/depois;
- deslocamento após o alerta;
- máximo avanço favorável;
- máximo avanço contrário;
- duração do movimento;
- regime de mercado;
- observações.

### 7. Validação estatística

A ferramenta deve responder, por exemplo:

- quantas vezes o alerta apareceu?
- em quantas vezes andou 4 pontos antes de andar 4 pontos contra?
- em quais horários funcionou melhor?
- em dias de notícia o padrão piorou ou melhorou?
- qual foi o tempo médio até o deslocamento?
- o sinal funcionou melhor com ou sem confluência de Volume At Price?

## Como estruturar o projeto nas próximas entregas

### Entrega 1 — Matriz de confluências

Criar uma tabela que relacione sinal, dados necessários, confluências, invalidação e referência.

Essa entrega define “o que é sinal de verdade” e “o que é ruído”.

### Entrega 2 — Catálogo de alertas

Definir os alertas que o produto vai emitir, com condições mínimas, confirmação, invalidação e severidade.

Essa entrega evita que a ferramenta vire um carnaval de alertas.

### Entrega 3 — Modelo de dados

Definir as entidades do motor:

- trade;
- agressão;
- book snapshot;
- volume por preço;
- delta;
- player activity;
- alert event;
- regime;
- score.

Essa entrega prepara o projeto para virar software.

### Entrega 4 — Protótipo com dados simulados

Criar um dashboard com dados simulados para testar os cenários:

- compra dominante;
- venda dominante;
- absorção;
- exaustão;
- rompimento;
- falso rompimento;
- wall;
- spoofing suspeito;
- fluxo climático.

Essa entrega valida a experiência antes da integração real.

### Entrega 5 — Metodologia de validação

Definir como medir se o alerta presta.

Essa entrega transforma o projeto de ferramenta visual em ferramenta de pesquisa operacional.

## Resposta prática: o que você deve me pedir agora

O melhor pedido agora seria:

> “Crie o rulebook executável e a arquitetura NTSL/ProfitPro da automação para WDO e WIN, com entrada, saída, proteção, bloqueios, notícias, fontes e auditoria.”

Esse pedido é melhor do que pedir “pesquisa aprofundada” de forma genérica, porque nos força a transformar pesquisa em produto.

## Como encaixar seu alvo de 4 pontos por entrada

O produto deve ter um modo chamado, por exemplo, **Scalp 4 Pontos**.

Esse modo não deve dizer “entre agora”. Ele deve avaliar:

- se o spread e liquidez permitem scalp curto;
- se o fluxo tem velocidade suficiente;
- se há região de alvo livre até 4 pontos;
- se o stop técnico não é maior que o alvo;
- se o sinal tem confluência suficiente;
- se o horário favorece movimento curto;
- se o risco de falso rompimento está alto.

Para ficar profissional, o produto deve bloquear ou rebaixar alertas quando o contexto não favorece esse tipo de scalp.

## Critério de qualidade profissional

A ferramenta só deve ser considerada profissional se conseguir responder:

1. Por que esse alerta apareceu?
2. Qual dado bruto sustentou o alerta?
3. Qual confluência confirmou?
4. Qual confluência faltou?
5. Onde o sinal é invalidado?
6. Qual é o risco de ruído?
7. Como esse padrão performou no replay?
8. O contexto atual combina com o objetivo de 4 pontos?

Se ela não responder isso, ela será apenas mais uma tela bonita.
