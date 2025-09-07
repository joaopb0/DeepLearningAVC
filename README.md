### Previsão de Acidente Vascular Cerebral (AVC) com Redes Neurais

#### 🎯 Sobre o Projeto

O Acidente Vascular Cerebral (AVC) é uma das principais causas de mortalidade e incapacidade em todo o mundo, tornando a sua previsão precoce um desafio crucial na área da saúde.

Este projeto teve como objetivo desenvolver um modelo de classificação, utilizando Redes Neurais Artificiais (Deep Learning), para prever a probabilidade de um paciente sofrer um AVC. A previsão foi baseada em dados demográficos, de saúde e de estilo de vida, utilizando o dataset *Stroke Prediction Dataset* da plataforma Kaggle.

#### 🛠️ Tecnologias Utilizadas

* **Linguagem de Programação:** Python
* **Análise e Manipulação de Dados:** Pandas, NumPy
* **Visualização de Dados:** Matplotlib, Seaborn
* **Machine Learning e Deep Learning:** Scikit-learn, TensorFlow (Keras)

#### ⚙️ Etapas do Projeto

**1. Análise e Tratamento dos Dados**

A qualidade do modelo começa na qualidade dos dados. Nesta etapa, tratei os dados com cuidado para garantir sua qualidade e consistência:

* **Limpeza de Dados:** Identifiquei e tratei valores ausentes na coluna `bmi` (índice de massa corporal), utilizando a mediana como uma abordagem robusta para o preenchimento.
* **Correção de Inconsistências:** Verifiquei erros lógicos nos dados, como a classificação incorreta do tipo de trabalho para crianças, e corrigi para a categoria "children".
* **Transformação de Variáveis:** Converti todas as colunas categóricas (como `gender`, `work_type`) para um formato numérico, um pré-requisito essencial para o treino da rede neural.

**2. Análise Exploratória de Dados (EDA)**

Para entender melhor os dados, fiz uma análise exploratória visual para encontrar os primeiros insights:

* **Dataset Desbalanceado:** A análise mostrou uma grande desproporção entre os casos de AVC (minoria) e não AVC (maioria), o que reforçou a importância de usar técnicas de balanceamento de classes no treino.
* **Correlação com Fatores de Risco:** Os gráficos comparativos mostraram que condições como **hipertensão** e **doenças cardíacas** estão associadas a uma maior percentagem de ocorrência de AVCs.
* **Distribuição de Variáveis Contínuas:** A análise da distribuição de variáveis como `avg_glucose_level` e `bmi` revelou padrões distintos entre os grupos de pacientes que tiveram e não tiveram AVC.

**3. Modelagem e Treino**

Para a tarefa de classificação, construí uma Rede Neural Artificial com Keras (TensorFlow). O meu foco foi criar um modelo que fosse não apenas preciso, mas também robusto e capaz de generalizar para novos dados:

* **Arquitetura da Rede:** O modelo é composto por uma camada de entrada, camadas ocultas com funções de ativação `ReLU` e `ELU`, e uma camada de saída com ativação `Sigmoid`, ideal para classificação binária.
* **Técnicas de Regularização:** Para combater o *overfitting*, apliquei duas técnicas essenciais:
    * **Dropout:** Para desativar neurónios aleatoriamente durante o treino, forçando a rede a aprender padrões mais robustos.
    * **Early Stopping:** Para monitorizar o treino e pará-lo no momento ideal, evitando o sobreajuste.
* **Balanceamento de Classes:** Devido à raridade de casos de AVC no dataset, apliquei a técnica de `class_weight='balanced'`. Isso fez com que o modelo desse mais importância aos casos de AVC durante o treino, o que é fundamental para evitar que eles fossem ignorados.

**4. Resultados e Avaliação do Modelo**

O modelo final alcançou uma acurácia de **75,6%** no conjunto de teste.

Contudo, para um problema de saúde, a acurácia geral pode ser uma métrica enganadora. Por isso, a avaliação focou-se em indicadores mais críticos:

* **Matriz de Confusão:** Analisei a matriz de erros e acertos do modelo, com foco especial em minimizar os **Falsos Negativos** — o erro mais crítico neste cenário, pois representa um paciente doente incorretamente classificado como saudável.
* **Recall (Sensibilidade):** O modelo alcançou um **recall de 77%** para a classe "AVC". Isto significa que ele foi capaz de identificar corretamente 77% de todos os pacientes que realmente tiveram um AVC.
* **Análise por Fatores de Risco:** O desempenho também foi analisado em subgrupos específicos, mostrando a eficácia do modelo em diferentes perfis de pacientes.

#### 🏁 Como Executar o Projeto

Este projeto foi desenvolvido em Google Colab e pode ser acessado e executado diretamente no seu navegador.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1QYnMndyvxHCaQ7yRKReCeWtcuRJax-3V)

**Instruções:**
1.  Clique no botão "Open in Colab" acima para abrir o notebook.
2.  Para que o download do dataset funcione, será necessário carregar a sua própria chave API do Kaggle (`kaggle.json`) no ambiente do Colab quando solicitado.
