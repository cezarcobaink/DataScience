# Airbnb em Buenos Aires — análise exploratória

**Dados:** 37.035 anúncios e 18 variáveis do [Inside Airbnb](http://insideairbnb.com/get-the-data/).

## Etapas

1. Dicionário de variáveis e verificação de tipos.
2. Porcentagem de valores ausentes por coluna.
3. Distribuições e identificação de outliers em preço e noites mínimas, com limites definidos pelo intervalo interquartil (IQR).
4. Limpeza da base e nova análise sem os outliers.
5. Correlação entre variáveis, tipos de imóvel e preço por bairro.

## Principais achados

- Cerca de **77% dos anúncios** são casas ou apartamentos inteiros.
- O **preço médio** é de cerca de 31.600 pesos argentinos por noite.
- **Puerto Madero** tem o maior preço médio e a menor oferta; **Palermo** e **Recoleta** têm preços menores e a maior oferta.
- A inflação alta na Argentina reduz a confiabilidade de comparações de preço ao longo do tempo.

**Stack:** Python · pandas · Matplotlib · Seaborn
