# Detecção de fraude em cartões de crédito

**Problema:** identificar transações fraudulentas em uma base onde a fraude é rara — apenas **0,17%** das 284.807 transações ([Credit Card Fraud Detection, Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)).

Com classes tão desbalanceadas, a acurácia engana: um modelo que diz "nunca é fraude" acerta 99,8%. Por isso o foco está em **recall** (quantas fraudes o modelo pega), **precisão** (quantos alertas são fraude de fato) e **ROC-AUC**.

## Como foi feito

1. **Análise exploratória** de valor e horário das transações, separando fraudes e transações normais.
2. **Separação de um conjunto de teste** (15% da base) antes de qualquer balanceamento, para avaliar o modelo em dados que ele nunca viu.
3. **Duas estratégias de balanceamento** no treino:
   - *Undersampling* baseado em clusters (K-Means) — reduz o treino a 710 exemplos balanceados.
   - *SMOTE* — gera exemplos sintéticos da classe minoritária.
4. **Dois modelos** para cada estratégia: árvore de decisão e regressão logística.

## Resultados (validação)

| Modelo | Balanceamento | Recall (fraude) | Precisão (fraude) | ROC-AUC |
|---|---|---|---|---|
| Árvore de decisão | Undersampling | 96,8% | 0,4% | 0,79 |
| Árvore de decisão | SMOTE | 76,2% | 38,1% | 0,88 |
| Regressão logística | Undersampling | 88,9% | 4,2% | 0,93 |
| Regressão logística | SMOTE | 87,3% | 5,7% | 0,92 |

No **conjunto de teste reservado**, a regressão logística chegou a **ROC-AUC de 0,95 (undersampling) e 0,96 (SMOTE)**.

## O que os números mostram

- Existe um **trade-off claro**: pegar quase todas as fraudes custa muitos alarmes falsos. A árvore com undersampling detecta 96,8% das fraudes, mas 99,6% dos seus alertas são falsos.
- A **árvore com SMOTE** tem o melhor equilíbrio entre recall e precisão (F1 de 0,51).
- A escolha final depende do custo do negócio: quanto custa uma fraude que passa, comparado a bloquear um cliente legítimo.

## Próximos passos

- Ajustar o limiar de decisão com base em uma curva precisão-recall e em custos reais.
- Testar modelos de gradient boosting (XGBoost, LightGBM).

## Como rodar

```bash
pip install -r requirements.txt
unzip creditcard.zip
jupyter notebook Deteccao_fraude_CC.ipynb
```

**Stack:** Python · pandas · scikit-learn · imbalanced-learn · Matplotlib · Seaborn
