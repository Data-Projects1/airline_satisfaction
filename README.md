# Previsão da satisfação de companhias aéreas

## Análise curva ROC

A avaliação da análise será com base na área sob a curva ROC (Receiver Operating Characteristic), para avaliar o desempenho de modelos de classificação de satisfação de forma binária na comparação do cálculo de probabilidade prevista e o resultado observado através de modelos de Machine Learning como Logistic Regression, Random Forest, XGBoost e LightGBM.

### Problema de Negócio

O resultado deve fazer a previsão da probabilidade para a variável de satisfação.

#### Base de Dados

train.csv - conjunto de treinamento, com a satisfação como alvo.<br/>
test.csv - conjunto de teste, utilizado para prever a probabilidade de satisfação.<br/>
sample_submission.csv - arquivo de submissão de exemplo no formato correto.<br/>

[Kaggle](https://www.kaggle.com/competitions/playground-series-s6e10/)

#### Campos de Dados

- id - ID que representa uma pesquisa de satisfação do conjunto de teste.<br/>
- Age - Idade do respondente.<br/>
- Flight Distance - Distância do vôo.<br/>
- Inflight wifi service - Satifação com o serviço de wifi disponibilidade.<br/>
- Departure/Arrival time convenient - Satifação com horário de conveniência do partida e chegada.<br/>
- Ease of Online booking - Satifação com Facilidade de reserva online.<br/>
- Gate location - Satifação com localização do portão de embarque.<br/>
- Food and drink - Satifação com comida e bebida a bordo.<br/>
- Online boarding - Satifação com serviço de check-in.<br/>
- Seat comfort - Satifação com conforto do assento.<br/>
- Inflight entertainment - Satifação com entretenimento a bordo.<br/>
- On-board service - Satifação com serviço a bordo.<br/>
- Leg room service - Satifação com serviço de espaço para as pernas.<br/>
- Baggage handling - Satifação com serviço de manuseio de bagagem.<br/>
- Checkin service - Satifação com serviço de check-in.<br/>
- Cleanliness - Satifação com limpeza.<br/>
- Departure Delay in Minutes - Atraso na partida em minutos.<br/>
- Arrival Delay in Minutes - Atraso na chegada em minutos.<br/>
- Gender - Gênero do respondente.<br/>
- Customer Type - Fidelização do respondente.<br/>
- Type of Travel - Tipo de viagem.<br/>
- Class - Classe do vôo.<br/>
- satisfaction - Resposta de satisfação em VERDADEIRO ou FALSO.<br/>

### Premissa de Negócio

### Estratégia de Solução

O objetivo do projeto é prever a satisfação do cliente em relação à compania aérea.
O modelo adotado busca prever a resposta de satisfação dos clientes que utilizaram os serviços da compania aérea.
O formato de entrega contém informações de ID do passageiro respondente da pesquisa e a previsão de resposta de satisfação.

#### Planejamento do Processo de Análise

O processo de desenvolvimento do projeto teve como base o método CRSIP-DM, aplicando os seguintes passos:
![CRISP_Process](/img/processo.png "Processo CRISP")

1. Questão do negócio:
   Identificação e entendimento do problema de negócio. Idendificar a resposta de satisfação dos passageiros respondentes da pesquisa em relação ao serviço da compania aérea.

2. Entendimento do negócio:
   Entendimento do core business do negócio a fim de identificar a melhor estratégia de análise a ser implementada e foco na resolução do problema.

3. Coleta de dados:
   Seleção de dados disponibilizados em 3 bases em formato csv (train.csv, test.csv e sample_submission.csv) no site Kaggle. Predicting Airline Satisfaction. Disponível em: <https://www.kaggle.com/competitions/playground-series-s6e10/data>. Acesso em: 01 out. 2026.

4. Limpeza de dados:
   Foram realizadas limpeza e tratamento de formatação dos dados de acordo com padrões documentados; padronização do formato dos títulos das variáveis; formatação do tipos e grandezas dos campos de análise; inclusão de valor de minutos no conjunto de dados de atraso de chegada cujas pesquisas não apresentavam informações no campo "arrival_delay_in_minutes"; tratamento ou remoção de campos vazios e remoção de atributo “id” cuja dimensão é irrelevante para a análise atual.

5. Exploração de dados:
   A etapa de exploração de dados consistiu no levantamento das hipóteses e análise descritiva dos dados para visão do cenário inicial de informações, volume de dados e seleção de variáveis numéricas e categóricas para análise univariada.
   Foi desenvolvido mapa mental de hipóteses para levantamento de trinte e uma hipóteses a serem validadas ou refutadas através da análise exploratória dos dados (EDA) nos campos do fenômeno analisado satisfação do cliente: serviços de conveniência, serviços a bordo e perfil do cliente.

![mind_map](/img/client_satisfaction.png "Mind Map")

Elementos de mapa mental de hipóteses:

- Fenômeno: campo a ser medido ou modelado (variável resposta = y);
- Agentes: agentes que impactam seu fenômeno (variáveis independentes = x);
- Atributos do agente: características dos atributos.

Hipóteses são geradas por:

- Surpresa: insight com hipóteses não analisadas;
- Teste de crença: verificar se a contraposição da crença é validada ou não. Isto é, validação da hipótese nula (H₀) ou da hipótese alternativa (H₁).

Das 22 hipóteses levantadas, 11 foram selecionadas para validação através de análises univariadas, bivariadas e multivariadas de variáveis numéricas e categóricas do conjunto.

#### 11 Hipóteses:

1.  Facilidade de autoserviço online de agendamento aumenta o nível de satisfação do cliente.
2.  O atraso na saída ou na chegada do vôo diminuem a satisfação do cliente.
3.  Distâncias maiores de vôo diminuem a satisfação do cliente.
4.  Quanto maior a satisfação com o serviço a bordo maior a satisfação do cliente.
5.  Quanto maior a satisfação com o serviço de wifi a bordo maior a satisfação do cliente.
6.  Quanto maior a satisfação com o serviço de entretenimento a bordo maior a satisfação do cliente.
7.  Quanto maior a satisfação com o conforto do assento maior a satisfação do cliente.
8.  Quanto maior a satisfação com o serviço de limpeza a bordo maior a satisfação do cliente.
9.  A classe de viajante Eco tem menor nível de satisfação.
10. O cliente fidelizado tem maior nível de satisfação.
11. Viajantes a trabalho tem maior nível de satisfação.

#### Top 3 Insights

H1 Facilidade de autoserviço online de agendamento aumenta o nível de satisfação do cliente.<br/>
**VERDADEIRA** A facilidade de autoserviço online de agendamento aumenta o nível de satisfação do cliente.<br/>
![hipótese1](/img/H1.png "Hipótese 1")<br/><br/>

H5 Quanto maior a satisfação com o serviço de wifi a bordo maior a satisfação do cliente.<br/>
**VERDADEIRA** Quanto maior a satisfação com serviço de wifi a bordo maior a satisfação do cliente.<br/>
![hipótese5](/img/H5.png "Hipótese 5")<br/><br/>
H11 Viajantes a trabalho tem maior nível de satisfação.<br/>
**VERDADEIRA** Viajantas a trabalho tem maior nível de satisfação.<br/>
![hipótese11](/img/H11.png "Hipótese 11")<br/><br/>

### Modelo de Machine Learning

A preparação dos dados numéricos consistiu em Rescaling para variáveis não Gaussianas, isto é, variáveis sem distribuição normal. Já para a transformação de variáveis categóricas em numéricas foram utilizados encodings mantendo a natureza do conjunto de dados para torná-las mensuráveis e One Hot Encoding para categorização binária (0,1) para cada variável resposta das categorias "gender", "customer_type", "type_of_travel", sendo 1 na label da variável a resposta positiva. Ordinal Encoding para categorização ordinal da categoria "class" de acordo com a graduação Eco=0, Eco Plus=1, Business=2.
Para a seleção de variáveis relevantes no modelo, foi aplicado para variáveis numéricas o método de matriz de correlação e para as variáveis categóricas o método Cramer's V, que associa a correlação entre duas variáveis categóricas baseada no teste Qui-Quadrado.<br/>
Matriz de Correlação - variáveis numéricas
![matriz_correlacao](/img/matriz_correlacao.png "Matriz Correlação")<br/>

Cramer's V - variáveis categóricas
![cramers_v](/img/cramesv.png "Cramer's V")<br/>

Ainda para seleção de variáveis relevantes para acurácia do modelo, foi aplicado o método Boruta. De acorod com os resultados sete variáveis independentes deveriam ser removidas da análise: "age", "arrival_delay_in_minutes", "departure_arrival_time_convenient", "departure_delay_in_minutes", "food_and_drink", "gate_location", "gender_Male".<br/>

#### Single Performance

A base de dados train.csv foi dividida em 80% treino e 20% validação, sendo treinado pela base treino e validado na base validação, de mesma estrutura porém com dados novos. Foram treinados quatro métodos de modelos: Logistic Regression, Random Forest Regressor, LightGBM, XGBoost Regressor. Sendo o Baseline Val (modelo de média) o modelo de referência para performance de comparação dos demais modelos. <br/>

- Métricas de Treino

  | Model                     | Accuracy | F1 Score | precision | Recall   | AUC      | ROC AUC  |
  | ------------------------- | -------- | -------- | --------- | -------- | -------- | -------- |
  | Baseline Train            | 0.500059 | 0.470344 | 0.443668  | 0.500433 | 0.500097 | 0.500097 |
  | Logistic Regression Train | 0.877515 | 0.859770 | 0.873452  | 0.846510 | 0.874371 | 0.920635 |
  | Random Forest Train       | 0.921952 | 0.912286 | 0.909569  | 0.915020 | 0.921249 | 0.959551 |
  | Light GBM Train           | 0.923515 | 0.913537 | 0.916178  | 0.910912 | 0.922237 | 0.958096 |
  | XGBoost Train             | 0.925897 | 0.916232 | 0.918856  | 0.913623 | 0.924652 | 0.962482 |

- Métricas de Validação

  | Model                          | Accuracy | F1 Score | precision | Recall   | AUC      | ROC AUC  |
  | ------------------------------ | -------- | -------- | --------- | -------- | -------- | -------- |
  | Baseline Val                   | 0.501240 | 0.471920 | 0.444914  | 0.502417 | 0.501359 | 0.501359 |
  | Logistic Regression Validation | 0.877129 | 0.859273 | 0.873305  | 0.845685 | 0.873940 | 0.919212 |
  | Random Forest Validation       | 0.918222 | 0.907990 | 0.906307  | 0.909680 | 0.917355 | 0.954362 |
  | Light GBM Validation           | 0.921352 | 0.910966 | 0.914897  | 0.907070 | 0.919904 | 0.955761 |
  | XGBoost Validation             | 0.921938 | 0.911650 | 0.915374  | 0.907956 | 0.920520 | 0.956250 |

#### Real Performance - Cross-Validation

- Métricas de comparação entre modelos (Cross Validation)

  | Model               | ROC AUC         | Log Loss        | Brier           | F1              |
  | ------------------- | --------------- | --------------- | --------------- | --------------- |
  | Logistic Regression | 0.9206 ± 0.0008 | 0.3464 ± 0.0019 | 0.0982 ± 0.0007 | 0.8597 ± 0.0010 |
  | Random Forest       | 0.9554 ± 0.0006 | 0.2423 ± 0.0021 | 0.0655 ± 0.0007 | 0.9093 ± 0.0011 |
  | Light GBM           | 0.9570 ± 0.0005 | 0.2346 ± 0.0019 | 0.0630 ± 0.0006 | 0.9130 ± 0.0007 |
  | XGBoost             | 0.9572 ± 0.0006 | 0.2339 ± 0.0018 | 0.0626 ± 0.0006 | 0.9137 ± 0.0008 |

Foi aplicado método de validação cruzada (Cross-Validation) sobre o conjunto de dados train.csv que foi dividido em cinco partes para que o modelo fosse treinado e avaliado repetidamente. Nesse processo a performance real do modelo foi o resultado da média de 3 cortes e desvio padrão do treino e validação. O que fornece uma estimativa mais robusta da capacidade de generalização do modelo.
Após análise dos modelos com menores valores de erro, os modelos Light GBM e XGBoost foram os que apresentaram melhores performances. Apesar do Random Forest ter menor erro, o modelo de XGBoost apresentou melhor capacidade de otimização de recursos se comparado ao modelo Random Forest.

### Machine Learning Performance

#### Hyperparameter Fine Tuning

A estratégia para definição do conjunto valores de hiperparâmetros (Hyperparameter Fine Tuning) para maximizar o aprendizado do modelo XGBoots foi a Randomized Search que testa combinações aleatórias no modelo de forma rápida e exige menor capacidade de processamento se comparado ao Grid Search.
Para o processo de cross-validation os dados de treinamento foram divididos em 3 partes em 20 combinações diferentes de hiperparâmetros. Totalizando 60 iterações no treinamento do modelo para identificação da melhor combinação de hiperparâmetros para cada parâmetro do modelo.
O fine tuning divide a base em 600 árvores, sendo utilizados em cada árvora 85% das amostras, 70% das colunas disponíveis na base, máximo de 127 e mínimo de 50 folhas.

Os hiperparâmetros que apresentaram a melhor performance para o modelo XGBoost foram:

| Parâmetro         | Valor |
| ----------------- | ----- |
| subsample         | 0.85  |
| num_leaves        | 127   |
| n_estimators      | 600   |
| min_child_samples | 50    |
| learning_rate     | 0.05  |
| colsample_bytree  | 0.7   |

-0.23143427073955536

#### Performance do Modelo

### Resultado de Negócios

#### Deploy

### Conclusões
