Disciplina de Inteligência Artificial , Professor Munif , Unicesumar 2026

# Previsão de Aprovação de Crédito com Machine Learning

## Integrantes
- Matheus Felipe Campioto Catenacci — RA: 22014137-2
- André Felipe Ferrari de Azevedo — RA: 22120196-2

---

## Resumo do Projeto

### Contextualização
A concessão de crédito é uma das atividades mais críticas do setor financeiro. Conceder crédito a um cliente de alto risco pode gerar prejuízos significativos, enquanto negar crédito a um bom pagador representa perda de receita. A inteligência artificial permite automatizar e tornar esse processo mais preciso e justo.

### Problema
Como prever se um cliente será um bom ou mau pagador com base em suas características financeiras e pessoais?

### Hipótese
É possível construir um modelo de IA capaz de classificar o risco de crédito de um cliente com acurácia superior a 70%, utilizando características como idade, valor do crédito, duração do empréstimo e histórico financeiro.

---

## Dataset

- **Nome:** German Credit Data
- **Origem:** UCI Machine Learning Repository / Kaggle
- **Link:** https://www.kaggle.com/datasets/uciml/german-credit
- **Registros:** 1.000 clientes
- **Atributos principais:**
  - Age (idade)
  - Sex (sexo)
  - Job (tipo de trabalho)
  - Housing (tipo de moradia)
  - Saving accounts (poupança)
  - Checking account (conta corrente)
  - Credit amount (valor do crédito)
  - Duration (duração em meses)
  - Purpose (finalidade do crédito)
- **Variável alvo:** Risk (good = bom pagador / bad = mau pagador)
- **Distribuição:** 70% bons pagadores / 30% maus pagadores
- **Preparação:** Remoção de nulos, codificação de variáveis categóricas com LabelEncoder, normalização com StandardScaler
- **Divisão:** 80% treino / 20% teste

---

## Métodos de IA Utilizados

### Parte 1 — Modelo Preditivo: Random Forest
Random Forest é um método de ensemble que cria múltiplas árvores de decisão independentes e combina suas previsões por votação majoritária. É robusto contra overfitting e lida bem com dados desbalanceados.

**Parâmetros utilizados:**
- n_estimators = 100 (número de árvores)
- random_state = 42

### Parte 2 — Modelo Descritivo: K-Means Clustering
K-Means é um algoritmo de agrupamento não supervisionado que segmenta os clientes em K grupos com características similares, sem usar a variável alvo. Utilizamos o método do cotovelo para determinar K=3 como o número ideal de clusters.

---

## Avaliação dos Modelos

### Random Forest — Métricas

| Métrica | Valor |
|---------|-------|
| Acurácia | ~75% |
| F1-Score | ~0.74 |
| Precisão | ~0.75 |
| Revocação | ~0.75 |

### Gráficos gerados
- `distribuicao_risco.png` — Distribuição da variável alvo
- `analise_exploratoria.png` — Análise de idade e crédito por risco
- `random_forest_resultados.png` — Matriz de confusão e importância das features
- `curva_acuracia_rf.png` — Acurácia por número de árvores
- `metodo_cotovelo.png` — Escolha do K ideal para K-Means
- `kmeans_resultados.png` — Clusters visualizados com PCA
- `comparacao_modelos.png` — Comparação entre modelos

---

## Comparação dos Resultados

| Modelo | Tipo | Acurácia | Objetivo |
|--------|------|----------|----------|
| Random Forest | Supervisionado (Preditivo) | ~75% | Classificar bom/mau pagador |
| K-Means | Não Supervisionado (Descritivo) | N/A | Segmentar perfis de clientes |

Os dois modelos se complementam: o Random Forest é ideal para decisões automatizadas de aprovação de crédito, enquanto o K-Means fornece insights estratégicos sobre perfis de clientes.

---

## Conclusão

O Random Forest demonstrou bom desempenho na classificação de risco de crédito. As features mais relevantes foram Duration, Credit amount e Age. O K-Means identificou 3 perfis distintos de clientes, revelando padrões úteis para estratégias de concessão de crédito. A combinação dos dois métodos oferece uma solução completa: predição automatizada + segmentação estratégica.

---

## Como Executar

1. Acesse o Google Colab: https://colab.research.google.com
2. Faça upload do arquivo `trabalho_ia_credito.ipynb`
3. Execute todas as células em ordem (Ctrl+F9)
4. Os gráficos e modelos serão gerados automaticamente

## Modelo Treinado

Os modelos treinados são salvos automaticamente ao executar o notebook:
- `modelo_random_forest.pkl` — Modelo Random Forest
- `modelo_kmeans.pkl` — Modelo K-Means
- `scaler.pkl` — Normalizador dos dados

## Estrutura do Repositório

```
├── trabalho_ia_credito.ipynb   # Notebook principal
├── german_credit_data.csv      # Dataset
├── modelo_random_forest.pkl    # Modelo treinado (gerado pelo notebook)
├── modelo_kmeans.pkl           # Modelo treinado (gerado pelo notebook)
├── scaler.pkl                  # Scaler (gerado pelo notebook)
├── README.md                   # Este arquivo
└── README.pdf                  # Versão PDF deste arquivo
```