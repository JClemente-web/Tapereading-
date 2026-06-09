# Visão de Produto: Ferramenta de Tape Reading para ProfitPro

## Proposta

Construir uma ferramenta de apoio operacional para traders que usam ProfitPro e operam Mini Dólar (WDO), com foco em leitura de fluxo, filtragem de ruído e geração de alertas claros.

A ferramenta deve complementar o ProfitPro, não substituir suas janelas nativas. A ideia é criar uma camada inteligente que organize sinais de Times & Trades, DOM, Footprint, Volume At Price e saldo de agressão em uma leitura objetiva.

## Problema

O trader de Tape Reading recebe muita informação simultânea:

- milhares de negócios em sequência;
- lotes pequenos irrelevantes;
- book mudando rapidamente;
- agressões que não geram deslocamento;
- rompimentos falsos;
- players atuando de forma fragmentada;
- alertas demais ou alertas pouco úteis.

Sem filtragem e contexto, o fluxo vira ruído.

## Objetivo do produto

Ajudar o trader a responder rapidamente:

- quem está agredindo agora?
- a agressão está gerando deslocamento ou sendo absorvida?
- existe desequilíbrio real entre compra e venda?
- há exaustão do movimento?
- o book mostra liquidez relevante ou possível manipulação?
- o rompimento tem fluxo ou é armadilha?
- há player relevante atuando de forma consistente?

## Princípios

1. **Clareza acima de excesso visual**: mostrar menos dados, mas com mais significado.
2. **Contexto antes de sinal**: nenhum print isolado deve gerar decisão automática.
3. **Fluxo validando preço**: sinais devem cruzar execução, book e deslocamento.
4. **Alertas acionáveis**: alertar apenas quando houver evento operacionalmente relevante.
5. **Estudo e replay**: permitir revisão pós-mercado para evolução do trader.
6. **Gestão de risco**: toda leitura deve informar também onde a tese deixa de fazer sentido.

## Módulos desejados

### 1. Motor de fluxo

Responsável por processar negócios, agressão, lotes, delta, saldo acumulado e intensidade.

Saídas esperadas:

- agressão compradora/vendedora;
- delta por janela;
- delta acumulado;
- intensidade do fluxo;
- velocidade de execução;
- lotes relevantes.

### 2. Detector de absorção

Identifica quando volume/agressão não gera deslocamento proporcional do preço.

Sinais possíveis:

- compra absorvida;
- venda absorvida;
- agressão sem deslocamento;
- defesa de preço;
- provável iceberg.

### 3. Detector de exaustão

Identifica perda de força do lado dominante.

Sinais possíveis:

- delta divergente;
- volume decrescente;
- agressão perdendo intensidade;
- fluxo climático seguido de pausa;
- possível reversão por fluxo.

### 4. Leitor de book

Monitora liquidez passiva e mudanças relevantes no DOM.

Sinais possíveis:

- wall;
- remoção brusca de liquidez;
- reposição;
- spoofing suspeito;
- escora institucional;
- desequilíbrio de profundidade.

### 5. Alert Engine

Transforma eventos em alertas objetivos.

Exemplos:

- ordem grande detectada;
- compra dominante;
- venda dominante;
- absorção provável;
- exaustão provável;
- rompimento com fluxo;
- falso rompimento provável;
- player relevante atuando.

### 6. Painel operacional

Interface resumida para o trader acompanhar:

- lado dominante;
- força do fluxo;
- principais eventos recentes;
- zonas de liquidez;
- alertas ativos;
- histórico curto dos sinais.

### 7. Diário e replay

Registro de eventos para estudo pós-mercado:

- horário;
- ativo;
- preço;
- sinal detectado;
- contexto;
- print/snapshot;
- entrada/saída do trader;
- resultado;
- observações.

## Diferencial esperado

O diferencial da ferramenta não deve ser simplesmente mostrar mais dados. O diferencial deve ser interpretar o fluxo em camadas:

1. dado bruto;
2. filtro de relevância;
3. evento de microestrutura;
4. contexto operacional;
5. alerta ou marcação para estudo.

## Público-alvo

- traders de WDO que usam ProfitPro;
- operadores de Tape Reading;
- scalpers;
- traders em formação que precisam estudar fluxo;
- mesas pequenas que desejam padronizar leitura operacional.

## Fora do escopo inicial

- robô autônomo de execução;
- promessa de sinal infalível;
- recomendação financeira;
- substituição total do ProfitPro;
- leitura de todos os ativos da B3 na primeira versão.
