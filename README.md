# **Projeto XAI: Interpretabilidade de modelos**

---

## Tema: **Predição de falhas e eventos de manutenção em máquinas industriais**

---
## **Roteiro**
---
### -  Pacotes
### 1. Dataset Escolhido
    - 1.1 Dataset: AI4I 2020 Predictive Maintenance Dataset
    - 1.2 Descrição Geral
    - 1.3 Estrutura do Dataset
    - 1.4 Contexto
    - 1.5 Carregando o Dataset

### 2. Exploração dos dados
    - 2.1 Informações do Dataset
    - 2.2 Matriz de Correlação
    - 2.3 Escolha do Target
    - 2.4 Estratégias para desbalanceamento das classes

### 3. Pré-processamento dos dados
    - 3.1 Convertendo variável categórica em numérica
    - 3.2 Normalização dos dados
### 4. Treinamento e Avaliação de Algoritmos
    - 4.1 Separação dos dados em treinamento e teste
    - 4.2 StratifiedKfold
    - 4.3 Modelos para treinamento
    - 4.4 RandomizedSearchCV
    - 4.5 Random Forest
    - 4.6 Logistic Regression
    - 4.7 Support Vector Machine
    - 4.8 Decision Trees

### 5. Global Surrogates
    - 5.1 Modelo caixa-preta e modelo caixa-branca 1
    - 5.2 Modelo caixa-preta e modelo caixa-branca 2
    - 5.3 Análise R-squared para os dois modelos Surrogates

### 6. Permutation Feature Importance (PFI)
    - 6.1 Modelo Random Forest
    - 6.2 PFI Classe minoritária (Falhou)
    - 6.3 Classe Majoritária (Não falhou)

### 7. Feature Selection
    - 7.1 Análise dos resultados

### 8. LIME
    - 8.1 Definindo modelo para o Lime
    - 8.2 Criando um explicador utilizando LIME nos dados de treinamento
    - 8.3 Selecionando Instância 1
    - 8.4 Selecionando Instância 2
    - 8.5 Selecionando Instância 3
    - 8.6 Selecionando Instância 4

### 9. Partial Dependence Plots
    - 9.1 Análise PDPs obtidos


### **1. Dataset Escolhido**

### 1.1. Dataset: AI4I 2020 Predictive Maintenance Dataset

O AI4I 2020 Predictive Maintenance Dataset está disponível no UCI Machine Learning Repository e foi desenvolvido para simular problemas de manutenção preditiva em processos industriais.

Link do dataset: https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset


### 1.2 Descrição Geral

Este dataset é destinado à predição de falhas e eventos de manutenção em máquinas industriais, focando em identificar padrões que indiquem necessidade de manutenção antes que falhas ocorram.


### 1.3 Estrutura do Dataset

| **Variável**                | **Tipo**           | **Descrição**                                              |
|-----------------------------|--------------------|------------------------------------------------------------|
|                   |
| |
| **Type**                    | Categórica         | Tipo de produto: `L`, `M`, `H` (baixo, médio e alto valor)  |
| **Air temperature [K]**      | Contínua (Numérica)| Temperatura do ar medida em Kelvin                         |
| **Process temperature [K]**  | Contínua (Numérica)| Temperatura do processo medida em Kelvin                   |
| **Rotational speed [rpm]**   | Contínua (Numérica)| Velocidade de rotação da máquina (RPM)                     |
| **Torque [Nm]**              | Contínua (Numérica)| Torque da máquina em Newton-metros                         |
| **Tool wear [min]**          | Contínua (Numérica)| Tempo de uso da ferramenta em minutos                      |

| **Target**                  | **Tipo**           | **Descrição**                                              |
|-----------------------------|--------------------|------------------------------------------------------------|
| **Machine failure**          | Binária            | Falha geral da máquina (`0` = Não, `1` = Sim)              |
| **TWF (Tool Wear Failure)**  | Binária            | Falha devido ao desgaste da ferramenta                     |
| **HDF (Heat Dissipation Failure)** | Binária      | Falha devido à dissipação inadequada de calor              |
| **PWF (Power Failure)**      | Binária            | Falha devido à falta de energia                            |
| **OSF (Overstrain Failure)** | Binária            | Falha causada por sobrecarga                               |
| **RNF (Random Failures)**    | Binária            | Falha aleatória sem causa específica                       |


O dataset é composto por 6 variáveis, sendo 1 variável categórica e 5 variáveis contínuas numéricas. Como alvo, tem-se 6 possíveis variáveis de saída, todas binárias. Portanto, é um dataset que permite a realização de análises aprofundadas dependendo do que se deseja predizer, e assim identificar padrões de possíveis falhas em máquinas industriais que possam vir acontecer.
