# WDO RESEARCH HARNESS — EXECUÇÃO CONTROLADA E AUDITÁVEL

## PAPEL

Atue como um Engenheiro Quantitativo Sênior.

Sua função NÃO é criar novas estratégias.

Sua função NÃO é otimizar parâmetros.

Sua função NÃO é sugerir indicadores.

Sua função NÃO é fazer pesquisa.

Sua função é executar exatamente o protocolo descrito abaixo e produzir artefatos auditáveis.

---

# CONTEXTO

Possuo:

1. Arquivo `wdo_harness.py`
2. Arquivo CSV exportado do Profit Pro contendo histórico do WDO
3. O harness já está implementado e validado conceitualmente

O objetivo é apenas verificar:

* Se o harness executa corretamente
* Se o CSV é carregado corretamente
* Se o backtest produz resultados reproduzíveis

---

# REGRAS OBRIGATÓRIAS

NÃO:

* alterar a estratégia
* alterar a lógica
* alterar parâmetros
* realizar grid search
* realizar otimização
* realizar walk-forward
* adicionar indicadores
* adicionar filtros
* modificar custos
* modificar slippage

Execute apenas o protocolo.

---

# ETAPA 0 — AUTO-TESTE

Executar:

```bash
python wdo_harness.py
```

Verificar se aparecem:

[1] PASSOU

[2] PASSOU

HARNESS VALIDADO

Se qualquer item falhar:

1. interromper imediatamente
2. informar erro completo
3. informar versões:

   * Python
   * pandas
   * numpy

Não prosseguir.

---

# ETAPA 1 — INSPEÇÃO DO CSV

Identificar automaticamente:

* encoding
* separador
* decimal
* nomes das colunas

Mostrar:

* cabeçalho
* primeiras 5 linhas

---

# ETAPA 2 — IMPORTAÇÃO

Construir a chamada correta de:

```python
load_csv(...)
```

compatível com o CSV real.

Executar:

```python
print(df.head())
print(df.dtypes)
print(df.shape)
```

Validar:

* datas corretas
* preços numéricos
* volume numérico

Se houver problema:

* parar
* explicar
* corrigir

---

# ETAPA 3 — FEATURES

Executar:

```python
df = add_features(df)
```

Mostrar:

```python
df.head()
```

Confirmar criação de:

* vwap
* atr
* dist_vwap
* rv
* is_ptax

---

# ETAPA 4 — REGIMES

Executar:

```python
df = add_regime(df)
```

Mostrar:

```python
df["regime"].value_counts(dropna=False)
```

Informar:

* quantidade de linhas válidas
* quantidade de linhas descartadas por warm-up

---

# ETAPA 5 — BACKTEST BASE

Executar:

```python
res = run_backtest(
    df,
    Params(
        exclude_ptax=False
    )
)
```

---

# ETAPA 6 — MÉTRICAS

Executar:

```python
summary = summarize(res["trades"])
```

Apresentar integralmente:

* n_trades
* expectancy
* profit_factor
* win_rate
* sharpe_daily_ann
* sortino_daily_ann
* max_dd_brl
* max_dd_pct
* total_net_brl
* avg_win
* avg_loss

---

# ETAPA 7 — BREAKDOWNS

Executar:

```python
breakdown(res["trades"], "regime")
```

Executar:

```python
breakdown(res["trades"], "touched_ptax")
```

Mostrar as tabelas completas.

---

# ETAPA 8 — BLOTTER

Exportar:

```python
res["trades"].to_csv("blotter.csv")
```

Informar:

* caminho do arquivo
* quantidade de trades

---

# ETAPA 9 — NOVEMBRO E DEZEMBRO DE 2024

Gerar análise separada contendo:

* trades em novembro de 2024
* trades em dezembro de 2024
* regimes observados
* quantidade de operações
* resultado financeiro

Não interpretar.

Apenas apresentar.

---

# ETAPA 10 — ENTREGA

Entregar somente:

1. Resultado do auto-teste
2. Configuração utilizada para carregar o CSV
3. Summary
4. Breakdown por regime
5. Breakdown PTAX
6. Quantidade de trades
7. Arquivo blotter.csv
8. Recorte Nov/2024
9. Recorte Dez/2024

Não concluir se a estratégia é boa.

Não concluir se a estratégia é ruim.

Não interpretar resultados.

Não otimizar.

Não modificar parâmetros.

Produzir apenas evidências reproduzíveis e auditáveis.
