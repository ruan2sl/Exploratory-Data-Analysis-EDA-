# Exploratory-Data-Analysis-EDA
Análise exploratória de dados para a disciplina de Ciência de Dados - CIN0208
# Análise Exploratória de Dados - Pima Indians Diabetes

Este projeto consiste em uma **Análise Exploratória de Dados (EDA)** detalhada sobre o famoso dataset *Pima Indians Diabetes*. O objetivo principal foi investigar os padrões clínicos e estatísticos que diferenciam pacientes diagnosticados com diabetes daqueles que não possuem a doença, além de preparar o terreno para futuros modelos de Machine Learning.

## 📊 Visão Geral do Dataset
O dataset, obtido via OpenML, contém dados de saúde de 768 pacientes do sexo feminino (pelo contexto original do dataset Pima), com 8 variáveis preditoras e 1 variável alvo.

* **Total de Instâncias:** 768
* **Variáveis (Features):** 8 (Gravidez, Glicose, Pressão, Pele, Insulina, IMC, Pedigree, Idade)
* **Target:** `class` (tested_positive / tested_negative)

## 💡 Principais Insights Obtidos

Durante a análise, foram levantados pontos críticos sobre a qualidade dos dados e o comportamento das variáveis:

### 1. O Problema dos "Dados Ocultos" (Zero-Missing)
Embora o dataset não apresente valores `NaN` explícitos, a análise descritiva revelou valores `0` biologicamente impossíveis em variáveis como:
* `plas` (Glicose)
* `pres` (Pressão Sanguínea)
* `skin` (Espessura da dobra cutânea)
* `insu` (Insulina)
* `mass` (IMC)

> **Conclusão:** Esses zeros representam dados faltantes e foram tratados antes da visualização avançada (UMAP) para evitar distorções.

### 2. Fatores Determinantes
A análise bivariada (Boxplots) mostrou que as variáveis com maior poder de distinção entre os grupos positivo e negativo são:
* **Glicose (`plas`):** A diferença mais significativa entre os grupos.
* **Idade (`age`) e IMC (`mass`):** Pacientes positivos tendem a ser mais velhos e possuir maior índice corporal.

### 3. Desbalanceamento de Classe
Identificou-se um desbalanceamento na variável alvo:
* **Negativos:** ~65%
* **Positivos:** ~35%
Isso sugere a necessidade de técnicas de balanceamento (como SMOTE ou class_weight) em etapas futuras de modelagem.

## 📈 Visualizações

### Distribuição das Features (Boxplot)
A visualização individualizada permitiu observar a separação das classes e a presença de outliers, especialmente na variável insulina.

![Boxplot das Features]()
*(Exemplo de análise: Note a clara separação na mediana da variável 'plas' entre os grupos)*

### Correlações (Heatmap)
A matriz de correlação de Pearson indicou baixa multicolinearidade severa (nenhuma correlação > 0.8), o que é positivo para modelos lineares. As maiores correlações observadas foram entre:
* Idade e Gravidez (0.54)
* IMC e Espessura da Pele (0.39)

![Matriz de Correlação]()

### Visualização Não-Linear (UMAP)
Utilizando a redução de dimensionalidade com UMAP (após tratamento de missing values e normalização), foi possível projetar os dados em 2D. Observou-se que, embora haja separação, existe uma zona de sobreposição complexa entre as classes, sugerindo que modelos lineares simples podem não ser suficientes.

![Projeção UMAP]()

## 🛠️ Tecnologias Utilizadas
* **Python** (Linguagem principal)
* **Pandas & NumPy** (Manipulação de dados)
* **Matplotlib & Seaborn** (Visualização estática)
* **Scikit-Learn** (Pré-processamento)
* **UMAP** (Redução de dimensionalidade e visualização de manifold)
