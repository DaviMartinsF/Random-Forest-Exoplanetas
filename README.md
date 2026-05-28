# Auditoria de Exoplanetas: Revisionismo via Machine Learning (Kepler)

Este repositório contém a implementação de um pipeline completo de Inteligência Artificial voltado para o revisionismo, auditoria e replicação de classificações no catálogo da missão Kepler (NASA). O objetivo central é utilizar técnicas de aprendizado de máquina para identificar e mitigar a incidência de falsos positivos astronômicos em dados consolidados.

---

## 🔭 Sobre o Projeto

Diferente de abordagens puramente voltadas à descoberta primária de novos corpos celestes, este trabalho foca na **auditoria científica**. Utilizamos uma abordagem híbrida que consome parâmetros físicos estruturados obtidos por técnicas de processamento de sinais e aplica modelos preditivos para validar a integridade de catálogos existentes. 

O sistema replica o processo de tomada de decisão científica, apontando convergências e isolando discrepâncias estatísticas onde métodos tradicionais de classificação possam ter falhado ou classificado eventos com menor grau de confiança.

---

## 🔄 Fluxo de Trabalho (Pipeline Concluído)

1. **Origem dos Parâmetros Estruturados:** O pipeline consome dados do Catálogo Cumulativo de Objetos de Interesse do Kepler (KOI) do *NASA Exoplanet Archive*. Atributos fundamentais como período orbital (`koi_period`), profundidade do trânsito (`koi_depth`) e Razão Sinal-Ruído (`koi_model_snr`) foram originalmente gerados via aplicação do algoritmo *Box Least Squares* (BLS) sobre as curvas de luz brutas.
2. **Saneamento e Engenharia de Dados:** Tratamento de inconsistências de formatação do arquivo por meio de rotinas em Python, manipulação de linhas malformadas (`on_bad_lines='skip'`), tipagem numérica estrita e descarte de valores nulos (`NaN`).
3. **Classificação Avançada via IA:** O conjunto de dados foi estratificado (80% treino / 20% teste) e submetido ao classificador **Random Forest**, parametrizado com balanceamento de classes (`class_weight='balanced'`) para neutralizar vieses volumétricos.
4. **Mapeamento de Explicabilidade:** Extração de métricas de importância de características (*Feature Importance*) para garantir que os critérios de tomada de decisão do modelo sejam fisicamente auditáveis por pares.

---

## 📊 Resultados de Performance (N2)

O modelo foi validado utilizando uma massa de teste contendo 1.829 registros equilibrados, alcançando uma **Acurácia Geral de 76,44%**. 

As métricas detalhadas revelam um comportamento preditivo perfeitamente simétrico e estável para ambas as classes analisadas:

### Métricas de Classificação

| Classe / Métrica | Precisão (*Precision*) | Revocação (*Recall*) | *F1-Score* | Suporte (*Support*) |
| :--- | :---: | :---: | :---: | :---: |
| **Falso Positivo** | 0,76 | 0,76 | 0,76 | 914 |
| **Planeta** | 0,76 | 0,76 | 0,76 | 915 |
| **Acurácia Geral** | — | — | **0,76** | **1.829** |

### Insights Científicos da Auditoria
* **Detecção de Anomalias:** A matriz de confusão isolou **216 casos de discrepância crítica** (falsos negativos do modelo). São registros rotulados originalmente pela NASA como falsos positivos, mas que o pipeline de IA classificou com assinaturas físicas equivalentes a planetas reais, cumprindo o objetivo de levantar alvos para revisão secundária.
* **Explicabilidade Prática:** O gráfico de *Feature Importance* confirmou empiricamente a premissa teórica do projeto: a **Razão Sinal-Ruído do Modelo (`koi_model_snr`)** destaca-se como o principal discriminador absoluto

 ## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python 3
* **Ambiente:** Google Colab / Jupyter Notebook
* **Manipulação de Dados:** Pandas
* **Inteligência Artificial:** Scikit-Learn (Classificadores, Divisão Estratificada e Métricas)
* **Visualização Estatística:** Matplotlib e Seaborn

---

## 👥 Autores e Identificação Acadêmica

* **Universidade Presbiteriana Mackenzie**
* **Faculdade de Computação e Informática (FCI)**
* **Disciplina:** Inteligência Artificial - 7°N CC (Noite)
* **Professor Orientador:** Dr. Ivan Carlos Alcântara de Oliveira
* **Integrante:** Davi Martins Figueiredo (RA: 10374878)

---
