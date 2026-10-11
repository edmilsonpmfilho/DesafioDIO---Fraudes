# DesafioDIO---Fraudes

# Exploração de Dados para indentificação de fraudes

###### Fraudes são raras -> modelo pode ignorar a classe 1, valor utilizado para a identificação das fraudes.


### Imports:
- StandardScaler - transformar os dados para que tenha media igual a 0 e desvio padrão igual a 1, para terem os valores na mesma escala.
- LogisticRegression - modelo de classificação, prever categoria, prever se é fraude class 1 ou não fraude class 0, serve baseline primeiro modelo pra inicar a analise
- classification_report - consegue ver as metricas mais importante para a classificação

#### LogisticRegression
  - Utilzado primeiro a forma padrão com 1000 inetrações, onde houve um aviso que não conseguiu convergir, com a quantidade passada, ou seja o erro que ele encontrou durante o processo estava sempre mudando, com isso o modelo encerrou os teste pois atingiu o limite estabelecido. Resultados de 0.84 no precision e 0.66 no recall
  - Utilizando o Solver=saga, que é comumente utilizado para grandres bases de dados,também não foi possivel encontrar uma solução, com a quantidade de interações solicitadas. Resultados, inexistentes utilizando este metodo
  - Utilizando o Solver=liblinear que é mais comum ser utilizado em bases de dados pequenas e medias, o sistema conseguiu finalizar dentro das mesmas 1000 interações.Resultados de precisão de 0.81 e 0.56 de recall.
  - Em ambos os casos a curva ROC, se manteve na mesma proporção.
  - Já a Precision-Recall Curve, existe um momento com o liblinear que é percebido um aumento continuo do recall com o precision, o que pode indicar que o modelo está conseguindo confirmar com mais exatidão as fraudes, contudo na terceira parte do grafico, a precisão começa a cair assim como no modelo padrão, o que indica que o modelo está começando a marcar todas as transações como fraude.

#### RandomForestClassifier
  - Já utilizando o RandomForestClassifier foi indentificado que com quanto mais arvores existem e mais profunda é a interação os numeros de fraudes ficam mais precisos, contudo o recall diminuit. Resultados 50 arvores e 10 de profundida temos, precision de 0.84 e recall de 0.76. 
  - Já com 500 arvores e 50 de profundidade temos, precision de 0.97 contudo um recall de apenas 0.70.

#### XGBClassifier
  - Utilizando o padrão passado temos uma precision de 0.94 e um recall de 0.78, seguindo este modelo, temos uma melhor apuração das fraudes reconlhecidas e um confirmação dentro dos parametros. 
  - Já na modificação do modelo onde controlamos a quantidade de linhas e colunas que cada arvore do é usada e com punição para erros temos uma precision de 0.89  e um recall de 0.79, que indica que ao limitar o uso completo dos dados obtidos e "punir" o modelo em caso de erros trouxe uma avaliação incompleta e imprecisa.

#### SHAP
  - podemos indentificar as principais variais que trouxeram grandes diferenciais para a analise de fraudes sendo elas as principais a V4 ea V14.

####### Ao executar o codigo é preciso ter cautela pois existem diferentes blocos de codigo que entregam variaveis de mesmo nome, onde cada bloco extra, apesar de trazer o mesmo modelo traz diferentes parametros que irão modificar o resultados que poderão ser utilizado futuramente.
