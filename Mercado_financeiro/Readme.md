# Mercados globais e Bitcoin, 2020–2024

**Pergunta:** como os principais mercados do mundo se comportaram da pandemia até meados de 2024 — e o quanto eles se movem juntos?

**Dados:** cotações diárias de jan/2020 a jun/2024 via Yahoo Finance (943 dias com negociação em todos os mercados).

| Mercado | Ativo |
|---|---|
| Brasil | Ibovespa (^BVSP) |
| EUA | S&P 500 (^GSPC) |
| Europa | Euro Stoxx 50 (^STOXX50E) |
| Japão | Nikkei 225 (^N225) |
| China | SSE Composite (000001.SS) |
| Cripto | Bitcoin (BTC-USD) |

## Principais achados

- **Volatilidade:** o Bitcoin teve **174 dias** com variação acima de 3%; os índices tiveram entre 7 (China) e 22 (Brasil).
- **Preços andam juntos no Ocidente e no Japão:** correlação de **0,93** entre EUA e Europa e **0,91** entre EUA e Japão.
- **O Brasil acompanha os EUA no dia a dia:** correlação de **0,61** entre os retornos diários do Ibovespa e do S&P 500.
- **A China segue um ciclo próprio:** correlação de preços baixa com todos os outros mercados (no máximo 0,29, com o Bitcoin).

## Técnicas

Retornos diários (`pct_change`), contagem de dias de alta e baixa volatilidade, correlação de Pearson entre preços e entre retornos, heatmaps e pairplots.

**Stack:** Python · pandas · yfinance · Matplotlib · Seaborn
