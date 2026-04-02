# Auditoria de Exoplanetas: Revisionismo via Machine Learning (Kepler)

[cite_start]Este repositório contém a implementação de um pipeline de **Inteligência Artificial** voltado para o revisionismo e a replicação de classificações no catálogo da missão Kepler (NASA)O objetivo central é utilizar técnicas de aprendizado de máquina para identificar e mitigar a incidência de **falsos positivos** em dados astronômicos consolidados.

## 🔭 Sobre o Projeto
Diferente de abordagens voltadas à descoberta de novos corpos celestes, este trabalho foca na **auditoria científica**. Utilizamos uma abordagem híbrida que combina o processamento de sinais clássico com modelos preditivos modernos para validar a integridade de catálogos existentes e replicar resultados oficiais com alta precisão.

### Fluxo de Trabalho (Pipeline)
1. **Extração de Atributos:** O algoritmo *Box Least Squares* (BLS) é aplicado às curvas de luz para extrair parâmetros físicos como período orbital e profundidade de trânsito.
2. **Filtragem por IA:** Os dados estruturados alimentam um modelo **Random Forest**, treinado para distinguir trânsitos planetários reais de ruídos instrumentais ou binárias eclipsantes.
3. **Análise de Confiabilidade:** Foco especial na **Razão Sinal-Ruído do Modelo** (`koi_model_snr`) como métrica primária para auditar a qualidade das detecções.

## 📊 Análise Exploratória (EDA)
Os principais marcos alcançados incluem:
* **Saneamento de Dados:** Limpeza e estruturação de atributos via `Pandas` e `Openpyxl`.
* **Visualização de Auditoria:** Gráficos de dispersão e *boxplots* comparando a Razão Sinal-Ruído entre as diferentes classes de objetos.
* **Identificação de Outliers:** Mapeamento de sinais de baixa confiança que justificam a aplicação do revisionismo algorítmico.

## 🛠️ Tecnologias Utilizadas
* **Linguagem:** Python 3
* **Ambiente:** JupyterNotebook
* **Bibliotecas:** * `Pandas` / `Openpyxl` (Manipulação de dados)
    * `Matplotlib` / `Seaborn` (Visualização de dados)
