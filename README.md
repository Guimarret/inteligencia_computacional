# 🌌 Classificação de Objetos Astronômicos com Técnicas de Inteligência Computacional  
### SDSS DR17 — Stars · Galaxies · Quasars

Este repositório contém o desenvolvimento completo da Atividade Final da disciplina **Inteligência Computacional**, cujo objetivo foi classificar automaticamente objetos astronômicos do catálogo **SDSS DR17** em três categorias: **STAR**, **GALAXY** e **QSO (Quasar)**.

O trabalho envolve pré-processamento de dados, engenharia de atributos, análise exploratória, modelagem com três abordagens distintas e otimização via GridSearchCV.

---

## 🎯 Objetivo do Projeto

O projeto visa comparar o desempenho de três modelos de aprendizado supervisionado:

- **Regressão Logística Multinomial**  
- **Árvore de Decisão**  
- **Random Forest (Ensemble)**  

A variável alvo é categórica, exigindo abordagem de classificação.

---

## 🧹 Pré-processamento e Engenharia de Atributos

- Remoção de colunas irrelevantes (metadados).  
- Exclusão de registros com valores inválidos (-9999).  
- Criação das **Cores Astronômicas**: `u-g`, `g-r`, `r-i`, `i-z`.  
- Normalização via *StandardScaler* para modelos lineares.  
- Divisão Treino/Teste: 80% / 20%.

---

## 🔍 Análise Exploratória (EDA)

Principais achados:

- **Redshift** é a variável com maior poder discriminativo.  
- Classe **STAR** é facilmente separável das demais.  
- Galáxias e Quasares apresentam sobreposição significativa.  
- Boxplots e histogramas confirmam padrões físicos esperados:
  - STAR → redshift ≈ 0  
  - GALAXY → intermediário  
  - QSO → valores altos  

---

## 🤖 Modelos Treinados e Grid Search

### 🔹 Regressão Logística
- GridSearch: `C = [0.1, 1, 10]`, solvers `lbfgs` e `saga`.  
- Limitação: fronteiras de decisão lineares.

### 🔹 Árvore de Decisão
- GridSearch: profundidade, critério (gini/entropy), min_samples_split.  
- Melhor desempenho não-linear individual.

### 🔹 Random Forest
- GridSearch: n_estimators, max_depth e critérios.  
- Melhor modelo e maior estabilidade.

---

## 📊 Resultados (Conjunto de Teste)

| Modelo               | Acurácia |
|----------------------|----------|
| Regressão Logística  | **95.77%** |
| Árvore de Decisão    | **97.47%** |
| Random Forest        | **97.96%** |

---

## 🧪 Validação Cruzada (k = 5)

| Modelo               | Média (%) | Desvio Padrão |
|----------------------|-----------|----------------|
| Regressão Logística  | 95.47%    | ±0.27% |
| Árvore de Decisão    | 97.28%    | ±0.30% |
| Random Forest        | **97.72%** | **±0.21%** |

---

## 🧠 Análise de Viés e Variância

### Regressão Logística
- **Alto viés**, baixa variância → underfitting.

### Árvore de Decisão
- Baixo viés, **variância moderada** → precisa de poda.

### Random Forest
- **Baixo viés + baixa variância** → ponto ótimo.  
- Reduz variância intrínseca das árvores via bagging.

---

## 🏆 Conclusão

O modelo **Random Forest otimizado** apresentou o melhor desempenho e robustez, atingindo:

- **97.96% de acurácia**  
- Menor desvio padrão na validação cruzada  
- Melhor generalização para novos dados  

O experimento demonstra que técnicas de ensemble são altamente eficazes para classificação de objetos astronômicos do SDSS DR17.

---

## 📜 Autores

- André Santos de Oliveira  
- Guilherme Esteves Marret  
- Gustavo Bueno  
- Sofia Costa Seijas Pena  
- Thiago Macedo Vaz