# Titanic

Datasets disponíveis no Kaggle: **["Titanic - Machine Learning from Disaster"](https://www.kaggle.com/competitions/titanic/overview)**.

### Parte 01: [Compreendendo e Manipulando Bases](https://github.com/nogueiraguilherme/Titanic/blob/main/Titanic_Parte_01.ipynb)

- Inicialmente fizemos a análise e manipulação básica para fazer uma submissão **sem** tratamento dos dados:
  - Para ter agilidade na compreensão das bases usamos o [ydata-profiling](https://github.com/ydataai/ydata-profiling), que retorna uma espécie de **resumo do dataset**;
  - Eliminamos colunas com **alta cardinalidade**;
  - Tratamos **valores vazios** substituindo pela média e a moda das variáveis correspondentes;
  - Eliminamos as **colunas de texto**;
  - Usamos 3 modelos de classificação: **Árvore de Classificação**, **KNN** e **Regressão Logística** e avaliamos os resultados desses modelos com a **acurácia** e a **matriz de confusão**;
- Resultado da submissão: **0.66746**.

### Parte 02: [Trabalhando com Colunas de Texto](https://github.com/nogueiraguilherme/Titanic/blob/main/Titanic_Parte_02.ipynb)
- Nesta etapa compreendemos e tratamos as colunas de texto para torná-las úteis no nosso modelo:
  - Utilizamos **lambda function** e **OneHotEncoder**;
- A classificação foi com os mesmos modelos vistos anteriormente;
- Resultado da submissão: **0.76555**.

### Parte 03: [Aplicando Engenharia de Recursos](https://github.com/nogueiraguilherme/Titanic/blob/main/Titanic_Parte_03.ipynb)
- Aqui fizemos uma manipulação profunda dos dados, buscando um melhor desempenho:
  - A escala dos dados **Age** e **Fare** foi ajustada;
  - Aprofundando análise nas colunas **SibSp** (irmãos/conjujes a bordo) e **Parch** (pais/filhos a bordo);
    - 2 colunas foram criadas: **Familiares** (total de familiares a bordo) e **Sozinho** (se o passageiro estava sozinho a bordo).
- Analisamos a correlação de todas as variáveis para selecionar aquelas que mais faziam sentido para o modelo:
  - Percebemos que a generalização da coluna **Embarked** não foi uma boa decisão;
  - Separamos os dados de embarque de acordo com o porto que o passageiro embarcou, para isso usamos o **OrdinalEncoder**
- A classificação foi com os mesmos modelos vistos anteriormente
- Resultado da submissão: **0.77751**

### Parte 04: [Testando Novos Modelos de Classificação](https://github.com/nogueiraguilherme/Titanic/blob/main/Titanic_Parte_04.ipynb)
- Nessa etapa final, fizemos a classificação com novos modelos, mantivemos a **Regressão Logística**, por ter apresentado os melhores resultados previamente, e adicionamos o **Random FOrest** e o **MLPClassifier**:
  - Mantivemos todas as colunas e utilizamos os novos classificadores para verificar os resultados apresentados.
  - A melhor acurácia na **validação** foi com o **MLPClassifier**, no entanto, nos dados de **teste** o resultado foi pior que o obtido na Parte 03, sugestivo de  overfitting.
- Resultado da submissão: **0.74880**

- Retomando o trabalho, utilizamos o **GridSearchCV** para estimar os melhores parâmetros para modelos que utilizamos na etapa anterior
- O modelo escolhido foi o **RandomForest** que apresentou melhora consideraval em relação a primeira etapa desta parte e também resultado melhor que na Parte 3.
- Resultado da submissão: **0.77990**
