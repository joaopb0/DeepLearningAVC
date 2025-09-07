### Previsão de Acidente Vascular Cerebral (AVC) com Redes Neuronais

#### 🎯 Sobre o Projeto

O Acidente Vascular Cerebral (AVC) é uma das principais causes de mortalidade e incapacidade em todo o mundo, tornando a sua previsão precoce um desafio crucial na área da saúde.

Este projeto tem como objetivo principal o desenvolvimento de um modelo de classificação, utilizando Redes Neurais Artificiais (Deep Learning), para prever a probabilidade de um paciente sofrer um AVC. A previsão baseia-se num conjunto de dados com informações demográficas, de saúde e de estilo de vida, proveniente do dataset *Stroke Prediction Dataset* da plataforma Kaggle.

#### 🛠️ Tecnologias Utilizadas

* **Linguagem de Programação:** Python
* **Análise e Manipulação de Dados:** Pandas, NumPy
* **Visualização de Dados:** Matplotlib, Seaborn
* **Machine Learning e Deep Learning:** Scikit-learn, TensorFlow (Keras)

#### ⚙️ Etapas do Projeto

**1. Análise e Tratamento dos Dados**

A qualidade do modelo começa na qualidade dos dados. Nesta etapa, foi realizado um tratamento cuidadoso para garantir a consistência e a robustez do dataset:

* **Limpeza de Dados:** Identificação e tratamento de valores ausentes na coluna `bmi` (índice de massa corporal), utilizando a mediana para preenchimento, uma abordagem robusta para dados com distribuição assimétrica.
* **Correção de Inconsistências:** Verificação de erros lógicos nos dados, como a classificação incorreta do tipo de trabalho para crianças, que foram devidamente corrigidos para a categoria "children".
* **Transformação de Variáveis:** Conversão de todas as colunas categóricas (ex: `gender`, `work_type`) para formato numérico, um pré-requisito essencial para o treino da rede neuronal.

**2. Análise Exploratória de Dados (EDA)**

Para compreender melhor a estrutura e as relações presentes nos dados, foi realizada uma análise exploratória visual. Os principais insights obtidos foram:

* **Dataset Desbalanceado:** Identificou-se uma grande desproporção entre os casos de AVC (minoria) e não AVC (maioria), o que reforçou a necessidade de técnicas de balanceamento de classes no treino do modelo.
* **Correlação com Fatores de Risco:** Gráficos comparativos mostraram que certas condições, como **hipertensão** e **doenças cardíacas**, estão associadas a uma maior percentagem de ocorrência de AVCs.
* **Distribuição de Variáveis Contínuas:** Análise da distribuição de variáveis como `avg_glucose_level` e `bmi` revelou padrões distintos entre os grupos de pacientes que tiveram e não tiveram AVC.

**3. Modelagem e Treino**

Para a tarefa de classificação, foi construída uma Rede Neuronal Artificial utilizando la biblioteca Keras (com TensorFlow). A escolha da arquitetura e dos parâmetros de treino visou não apenas a acurácia, mas também a criação de um modelo robusto e generalizável:

* **Arquitetura da Rede:** O modelo é composto por uma camada de entrada, camadas ocultas com funções de ativação `ReLU` e `ELU` para aprender padrões complexos, e uma camada de saída com ativação `Sigmoid`, adequada para a classificação binária (AVC ou não AVC).
* **Técnicas de Regularização:** Para evitar o sobreajustamento (*overfitting*) e garantir que o modelo se comporte bem com dados novos, foram aplicadas duas técnicas essenciais:
    * **Dropout:** Uma camada de `Dropout` foi incluída para desativar aleatoriamente uma percentagem de neurónios durante o treino, forçando a rede a aprender padrões mais robustos.
    * **Early Stopping:** O treino foi monitorizado para parar automaticamente caso o desempenho no conjunto de validação não melhorasse, garantindo o ponto ótimo de treino.
* **Balanceamento de Classes:** Devido à baixa representatividade de casos positivos de AVC no dataset, foi aplicada a técnica de `class_weight='balanced'`. Isto ajusta os pesos durante o treino, dando mais importância à classe minoritária e reduzindo o risco de o modelo simplesmente "ignorar" os casos de AVC.

**4. Resultados e Avaliação do Modelo**

O modelo final alcançou uma acurácia de **75,6%** no conjunto de teste.

No entanto, em problemas de diagnóstico médico, a acurácia geral pode ser uma métrica insuficiente. Por isso, a avaliação focou-se em métricas mais críticas para o contexto do problema:

* **Matriz de Confusão:** Foi gerada uma matriz para visualizar os acertos e erros do modelo. A análise focou em minimizar os **Falsos Negativos** (pacientes com AVC classificados como saudáveis), que representam o erro mais crítico neste cenário.
* **Recall (Sensibilidade):** Graças ao balanceamento de classes, o modelo alcançou um **recall de 77%** para os casos de AVC. Isto significa que ele foi capaz de identificar corretamente 77% de todos os pacientes que realmente tiveram um AVC no conjunto de teste.
* **Análise por Fatores de Risco:** O desempenho foi analisado em diferentes subgrupos, mostrando a capacidade do modelo de prever o risco tanto em pacientes com fatores de risco conhecidos quanto naqueles sem histórico aparente.

#### 🏁 Como Executar o Projeto

Este projeto foi desenvolvido utilizando Google Colab e pode ser acedido e executado diretamente no seu navegador.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1QYnMndyvxHCaQ7yRKReCeWtcuRJax-3V)

**Instruções:**
1.  Clique no botão "Open in Colab" acima para abrir o notebook.
2.  Para que o download do dataset do Kaggle funcione, será necessário carregar a sua própria chave API do Kaggle (`kaggle.json`) para o ambiente do Colab quando solicitado pelo código.
