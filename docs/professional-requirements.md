# Requisitos Profissionais da Ferramenta

## Objetivo

Definir o que a ferramenta precisa ter para não se tornar banal. O padrão desejado é de uma ferramenta de apoio a decisão, pesquisa e replay, semelhante ao que uma mesa profissional esperaria de uma solução interna.

## Requisitos de produto

### PR-001 — Classificação de regime

A ferramenta deve classificar o mercado antes de priorizar alertas.

Regimes iniciais:

- tendência de alta;
- tendência de baixa;
- lateral;
- abertura volátil;
- notícia/macro;
- baixa liquidez;
- fluxo climático;
- consolidação;
- pós-rompimento;
- pré-ajuste.

### PR-002 — Alertas contextuais

A ferramenta deve gerar alertas com contexto, não apenas gatilhos.

Cada alerta deve conter:

- nome;
- lado;
- preço;
- horário;
- score;
- confluências presentes;
- confluências ausentes;
- invalidação;
- risco de falso positivo;
- compatibilidade com modo operacional.

### PR-003 — Modo Scalp 4 Pontos

A ferramenta deve permitir um modo operacional focado em movimentos curtos de 4 pontos.

O modo deve avaliar:

- espaço até alvo;
- liquidez no caminho;
- eficiência do fluxo;
- stop técnico provável;
- velocidade do mercado;
- risco de ruído;
- presença de barreira contra o trade.

O modo pode executar automaticamente somente quando o ambiente estiver compatível com a busca de scalp curto e todas as regras de entrada, proteção, bloqueio, limite diário e auditoria estiverem satisfeitas.

### PR-004 — Motor de eficiência do fluxo

A ferramenta deve medir se a agressão gera deslocamento.

Entradas:

- volume agressor;
- delta;
- deslocamento em ticks;
- tempo;
- liquidez consumida;
- liquidez reposta.

Saídas:

- fluxo eficiente;
- fluxo absorvido;
- fluxo divergente;
- fluxo climático;
- fluxo ruidoso.

### PR-005 — Leitura de book multi-nível

A ferramenta deve considerar mais de um nível do book quando houver dados disponíveis.

Métricas candidatas:

- desequilíbrio top-of-book;
- desequilíbrio em 5 níveis;
- desequilíbrio em 10 níveis;
- parede relativa;
- remoção de liquidez;
- reposição;
- cancelamento suspeito.

### PR-006 — Replay e auditoria

Todo alerta deve ser salvo para estudo.

Campos mínimos:

- id;
- timestamp;
- ativo;
- preço;
- tipo de alerta;
- score;
- regime;
- confluências;
- invalidação;
- deslocamento após 5s, 10s, 30s e 60s;
- máximo avanço favorável;
- máximo avanço contrário;
- resultado estatístico do evento.

### PR-007 — Biblioteca de referências

Cada regra importante deve apontar para uma fonte ou hipótese documentada.

Categorias:

- oficial;
- funcional;
- acadêmica;
- hipótese operacional;
- validação própria.

### PR-008 — Parametrização por perfil

A ferramenta deve permitir perfis.

Perfis iniciais:

- conservador;
- balanceado;
- agressivo;
- alta volatilidade;
- baixa liquidez;
- scalp 4 pontos.

### PR-009 — Gestão de risco informativa

A ferramenta deve exibir risco e invalidação, não apenas oportunidade.

Para cada alerta:

- onde a tese falha;
- qual barreira está contra;
- se o alvo de 4 pontos está livre;
- se o stop técnico parece maior que o alvo;
- se o sinal está atrasado.

### PR-010 — Separação entre sinal e decisão

O sistema deve separar claramente:

- dado bruto;
- evento detectado;
- confluência;
- alerta;
- decisão do trader;
- resultado medido.

## Requisitos de pesquisa

### RQ-001 — Validação por horário

Cada sinal deve ser avaliado por faixa de horário:

- abertura;
- abertura dos EUA;
- almoço;
- tarde;
- ajuste/final.

### RQ-002 — Validação por regime

O mesmo sinal deve ser medido separadamente em tendência, lateralidade, notícia e baixa liquidez.

### RQ-003 — Métrica de 4 pontos

Para cada alerta, medir:

- atingiu 4 pontos a favor antes de 4 pontos contra?
- tempo até atingir 4 pontos;
- máximo contra antes de atingir 4 pontos;
- frequência por horário;
- frequência por regime.

### RQ-004 — Falso positivo

Todo alerta deve ter métrica de falso positivo.

Exemplos:

- alerta de rompimento que volta para dentro da faixa;
- alerta de absorção que vira rompimento;
- alerta de exaustão que vira continuação;
- alerta de wall que some sem reação útil.

## Requisitos de interface

### UI-001 — Painel principal

O painel principal deve mostrar em poucos segundos:

- lado dominante;
- força do fluxo;
- score de ruído;
- alertas recentes;
- região de invalidação;
- compatibilidade com scalp 4 pontos.

### UI-002 — Timeline de eventos

A timeline deve listar eventos em ordem temporal, com severidade e confluências.

### UI-003 — Mapa de liquidez

Deve mostrar regiões próximas que podem impedir ou facilitar o deslocamento de 4 pontos.

### UI-004 — Replay

Deve permitir revisar sessão, filtrar alertas e comparar com deslocamento posterior.

## Critério de não banalidade

A ferramenta será considerada banal se:

- gerar alerta por print isolado;
- ignorar regime de mercado;
- não explicar a razão do alerta;
- não registrar resultado;
- não tiver invalidação;
- não medir falso positivo;
- não diferenciar oportunidade de ruído;
- prometer entrada em vez de classificar contexto.

A ferramenta será considerada profissional se:

- justificar cada alerta;
- cruzar dados independentes;
- medir performance dos sinais;
- adaptar parâmetros ao regime;
- registrar replay;
- ajudar o trader a evitar trades ruins, não apenas buscar entradas.

## Requisitos contra caixa-preta

A automação não deve funcionar como uma ferramenta opinativa ou de caixa-preta. Ela deve funcionar por regras explícitas, auditáveis e reproduzíveis.

### BB-001 — Sem decisão sem explicação

Toda execução deve explicar:

- qual regra foi acionada;
- quais dados confirmaram;
- quais dados bloqueariam;
- qual fonte sustenta a regra;
- qual proteção foi enviada;
- qual condição encerra a posição.

### BB-002 — Sem regra sem fonte

Nenhuma regra pode ser implementada apenas por opinião. Cada regra precisa estar conectada a:

- fonte oficial;
- documentação da plataforma;
- pesquisa acadêmica;
- validação própria por replay/backtest/log;
- revisão de risco.

### BB-003 — Sem automação sem kill switch

A automação deve ter mecanismo de parada por:

- perda diária;
- ganho diário;
- falha de dados;
- rejeição de ordem;
- notícia crítica;
- slippage anormal;
- inconsistência de posição;
- comando manual.

### BB-004 — Sem aprendizado não supervisionado em produção

Qualquer modelo estatístico ou componente adaptativo deve operar primeiro em modo observador. Mudanças automáticas de parâmetro em produção só podem ocorrer se houver regra documentada, limite, log e aprovação.
