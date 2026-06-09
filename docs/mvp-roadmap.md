# MVP e Roadmap

## Objetivo do MVP

Validar uma primeira versão da ferramenta com foco em leitura objetiva de fluxo para WDO, usando conceitos de Tape Reading aplicados ao ambiente ProfitPro.

O MVP deve priorizar organização, documentação do domínio, simulação de sinais e criação de uma base para implementação futura.

## Hipóteses do MVP

1. Traders precisam reduzir ruído no Times & Trades.
2. Alertas simples de agressão e absorção já geram valor operacional.
3. Uma visão consolidada de delta, intensidade e deslocamento ajuda na tomada de decisão.
4. Replay e registro de eventos ajudam o trader a evoluir mais rápido.

## Fase 1: Base conceitual

Entregáveis:

- documentação de fundamentos de Tape Reading em WDO;
- definição dos principais eventos de fluxo;
- glossário operacional;
- visão de produto;
- critérios iniciais de MVP.

Status: iniciado.

## Fase 2: Modelo de eventos

Criar uma estrutura de eventos para representar o fluxo.

Eventos candidatos:

- trade executado;
- agressão compradora;
- agressão vendedora;
- lote relevante;
- delta positivo/negativo;
- imbalance;
- absorção;
- exaustão;
- wall;
- remoção de liquidez;
- spoofing suspeito;
- rompimento confirmado;
- falso rompimento provável.

Critério de aceite:

- cada evento deve ter definição clara;
- cada evento deve ter parâmetros mínimos;
- cada evento deve permitir classificação por severidade/relevância.

## Fase 3: Protótipo visual

Criar um dashboard inicial, mesmo que com dados simulados.

Componentes sugeridos:

- painel de agressão atual;
- delta por janela;
- lista de eventos recentes;
- força compradora/vendedora;
- alertas visuais;
- zonas de preço monitoradas.

Critério de aceite:

- o usuário consegue entender o lado dominante em poucos segundos;
- eventos aparecem em ordem temporal;
- alertas não poluem a tela.

## Fase 4: Simulador de fluxo

Criar dados simulados para testar regras de leitura.

Cenários simulados:

- compra dominante com deslocamento;
- venda dominante com deslocamento;
- compra absorvida;
- venda absorvida;
- rompimento válido;
- falso rompimento;
- exaustão após movimento forte;
- fluxo climático;
- wall no book;
- spoofing suspeito.

Critério de aceite:

- cada cenário deve gerar eventos compatíveis com a tese;
- o simulador deve permitir teste sem depender de integração real com ProfitPro.

## Fase 5: Integração futura

Mapear possibilidades de integração com dados reais ou exportados.

Caminhos possíveis:

- arquivos exportados;
- captura estruturada de logs;
- integração com APIs disponíveis;
- processamento de dados de mercado de provedores externos;
- scripts/indicadores customizados quando aplicável.

Critério de aceite:

- definir caminho tecnicamente viável;
- documentar limitações;
- evitar dependência de recurso não confirmado.

## Métricas de sucesso

- redução de ruído percebido pelo trader;
- clareza dos alertas;
- consistência na identificação de absorção e exaustão;
- utilidade no replay pós-mercado;
- facilidade de configurar parâmetros por perfil operacional.

## Parâmetros iniciais sugeridos

Os valores abaixo são apenas referências iniciais e devem ser ajustados ao contexto do dia:

- lote mínimo para destaque: 5 a 10 contratos;
- lote relevante: 50 contratos;
- lote grande: 100 a 500 contratos;
- evento extraordinário: 1000+ contratos;
- imbalance inicial: 2x ou maior;
- janela curta de leitura: 1s a 10s;
- janela de contexto: 1min a 5min.

## Riscos do produto

- excesso de alertas;
- falsa sensação de precisão;
- dependência de dados não disponíveis;
- interpretação incorreta de spoofing/iceberg;
- overfitting em padrões de um único período;
- incentivo ao overtrading.

## Próxima decisão técnica

A próxima decisão é escolher o formato do primeiro protótipo:

1. dashboard web com dados simulados;
2. biblioteca de motor de fluxo;
3. documentação + glossário + regras;
4. integração com dados exportados.

A recomendação inicial é começar por dashboard web com dados simulados e motor de eventos simples, porque isso permite validar a experiência antes de depender de integração real.
