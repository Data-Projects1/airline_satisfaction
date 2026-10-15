# Previsão da satisfação de companhias aéreas

## Análise curva ROC

A avaliação da análise será com base na área sob a curva ROC (Receiver Operating Characteristic), para avaliar o desempenho de modelos de classificação de satisfação de forma binária na comparação do cálculo de probabilidade prevista e o resultado observado através de modelos de Machine Learning como Logistic Regression, Random Forest, XGBoost e LightGBM.

### Problema de Negócio

O resultado deve fazer a previsão da probabilidade para a variável de satisfação.

#### Base de Dados

train.csv - conjunto de treinamento, com a satisfação como alvo
test.csv - conjunto de teste, utilizado para prever a probabilidade de satisfação
sample_submission.csv - arquivo de submissão de exemplo no formato correto

[Kaggle](https://www.kaggle.com/competitions/rossmann-store-sales/data)

#### Campos de Dados

id - ID que representa uma pesquisa de satisfação do conjunto de teste.<br>
Age - Idade do respondente.<br>
Flight Distance - Distância do vôo.<br>
Inflight wifi service - Satifação com o serviço de wifi disponibilidade.<br>
Departure/Arrival time convenient - Satifação com horário de conveniência do parida e chegada.<br>
Ease of Online booking - Satifação com facilidade de agendamento.<br>
Gate location - Satifação com localização do portão de embarque.<br>
Food and drink - Satifação com comida e bebida a bordo.<br>
Online boarding - Satifação com serviço de check-in.<br>
Seat comfort - Satifação com conforto do asento.<br>
Inflight entertainment - Satifação com entretenimento a bordo.<br>
On-board service - Satifação com serviço a bordo.<br>
Leg room service - Satifação com serviço de espaço para as pernas.<br>
Baggage handling - Satifação com manuseio de bagagem.<br>
Checkin service - Satifação com serviço de check-in.<br>
Cleanliness - Satifação com limpeza.<br>
Departure Delay in Minutes - Atraso na partida em minutos.<br>
Arrival Delay in Minutes - Atraso na chegada em minutos.<br>
Gender - Gênero do resondente.<br>
Customer Type - Fidelização do repsondente.<br>
Type of Travel - Tipo de viagem.<br>
Class - Classe do vôo.<br>
satisfaction - Resposta de satifação em VERDADEIRO ou FALSO.<br>

### Premissa de Negócio

### Estratégia de Solução

#### Planejamento do Processo de Análise

#### Hipóteses:

#### Top 3 Insights

### Modelo de Machile Learning

#### Single Performance

#### Real Performance - Cross Validation

### Machine Learning Performance

#### Hyperparameter Fine Tuning

#### Performance do Modelo

### Resultado de Negócios

#### Deploy

### Conclusões
