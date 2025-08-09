# Telecom X - Parte 2: Análise Preditiva de Churn

## Propósito da Análise

Este projeto tem como objetivo principal **prever o churn (evasão) de clientes** da empresa Telecom X, utilizando variáveis relevantes para identificar quais fatores influenciam a decisão dos clientes de cancelar seus serviços. A partir disso, buscamos construir modelos preditivos eficientes que apoiem estratégias de retenção e melhorias no negócio.

---

## Estrutura do Projeto

- `TelecomX_parte2.ipynb` — Notebook principal que contém toda a análise exploratória, preparação dos dados, modelagem e avaliação dos modelos.  
- `dados_tratados.csv` — Arquivo CSV com os dados já tratados e prontos para análise, disponível no repositório (link direto no notebook).  

---

## Preparação dos Dados

### Classificação das Variáveis

- **Variáveis categóricas:** Informações qualitativas, como tipo de serviço contratado, método de pagamento, presença de serviços adicionais, gênero, etc.  
- **Variáveis numéricas:** Dados quantitativos, como tempo de contrato (`tenure`), valor mensal pago (`Charges.Monthly`), idade (ex: `SeniorCitizen`).

### Tratamento e Codificação

- Colunas irrelevantes e com alta cardinalidade (possíveis identificadores únicos) foram removidas para evitar viés e redundância.  
- Variável alvo `Churn` foi convertida para formato binário (0 = cliente ativo, 1 = evadido).  
- Aplicação de **one-hot encoding** nas variáveis categóricas para transformar os dados em formato numérico compatível com os algoritmos de machine learning.  
- Utilização da técnica **SMOTE** para balancear as classes, gerando exemplos sintéticos da classe minoritária e garantindo melhor treinamento dos modelos.

### Normalização

- A normalização foi aplicada somente para o modelo de **Regressão Logística**, que é sensível à escala dos dados.  
- Modelos baseados em árvore, como **Random Forest**, não necessitam dessa etapa, pois são insensíveis à escala.

### Separação dos Dados

- O dataset balanceado foi dividido em **80% para treino** e **20% para teste**, com estratificação para manter a proporção equilibrada das classes entre os conjuntos.

---

## Justificativas das Escolhas de Modelagem

- **Regressão Logística:** Modelo linear, interpretável, sensível à escala dos dados — por isso a padronização foi aplicada.  
- **Random Forest:** Modelo baseado em árvores, robusto a outliers e relações não lineares, não requer normalização, e geralmente apresenta bom desempenho em problemas de classificação com dados tabulares.

---

## Exemplos de Gráficos e Insights (EDA)

- **Matriz de correlação:** Identificou que `tenure` (tempo de contrato) tem correlação negativa com churn (-0.35), indicando que clientes mais antigos têm menor propensão a evadir.  
- **Boxplots:**  
  - Distribuição de `tenure` por churn mostra que clientes evadidos possuem em geral menor tempo de contrato.  
  - Distribuição de `Charges.Monthly` sugere que clientes com cobranças mensais maiores tendem a permanecer, porém existe maior variabilidade na classe de evadidos.  

Esses insights apoiam as conclusões extraídas dos modelos e embasam recomendações para retenção.

---

## Como Executar o Notebook

### Requisitos

- Python 3.x  
- Bibliotecas Python:  
  - pandas  
  - numpy  
  - scikit-learn  
  - imbalanced-learn  
  - matplotlib  
  - seaborn  

Você pode instalar todas as dependências com:  
```bash
pip install pandas numpy scikit-learn imbalanced-learn matplotlib seaborn
