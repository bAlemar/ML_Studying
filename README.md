# ML_Studying
## Meu estudos de Machine learning e coisas desse tipo
Primeiro tópico é ##Matrix Confusion## 
#Iremos ver como analisar uma matriz de confusão e como tomar cuidado com classes desbalanceadas.


##MATRIX CONFUSION##
#Medir performance de modelos de classificação, ajuda a entender o desempenho de um classificador #Matriz N x N , composta pelos valores preditos e os verdadeiros valores.

#True Positive(TP): #O valor preditivo é positivo e o valor real é positivo também #True Negative(TN): #Valor preditivo é negativo e o valor real é negativo também #False Positive(FP) - Type 1 error: #Valor preditivo é positivo e o valor real,entranto é negativo #False Negative(FN) - Type 2 error: #Valor preditivo é negativo e o valo real,entreanto é positivo

#Sabendo desses conceitos iremos, relacionarmos e criaremos métricas: #Contexto: # Para isso iremos tomar como exemplo uma Matrix de Correlação de um modelo de previsão # para pessoas doentes(positive) ou não(negative).

#Lembrando linhas: Predict , colunas: Real

[560,60]
[50,330]
#1o passo: #Identificar os valores: #TP = 560 ; TN = 330 ; #FP = 60 ; #FN = 50

#Accuracy = TP + TN / (TP + FP + TN + FN)

96%
#OBS : # Temos class imbalanced dataset: 947 targets negatives and only 3 targets positives #Ao calcular accuracy pensamos, nosso modelo tem 96% de acurácia em prever se as pessoas estão #doentes ou não... Entreanto, é exatamente ao contrário, 96% acurácia em prever pessoas não doentes. #Nesse contexto, devemos focar em prever os resultados positivos corretamente. #Desse modo iremos trabalhar com 2 novas métricas: Precision vs Recall.

##Precision = TP / TP + FP #Quantos casos preditos como positivos, são realmente positivos #90% #Ou seja, 90% da previsão de casos positivos são realmente positivos. #Precision é útil quando nossa preocupação maior é em cima dos falsos negativos, ou seja #valores que foram previstos como negativos quando na verdade eram positivos. #Por exemplo, num sistema de recomendação de música,e-commerce etc... devemos focar na Precision. #Onde resultados errados podem levar a perde de clientes e prejudicar o negócio.

Recall/Sensitivy/TPR = TP / TP + FN
#Quantos casos preditos como positivos o modelo é capaz de prever. #91% dos valores positivos são previstos pelo nosso modelo. #Recall é útil quando Falso Negativo supera o Falso Positivo, ou seja (??) #Nosso modelo está (??) #Por exemplo, num casos médicos em que é irrelevante dispararmos um alarme falso, entretanto #casos positivos não podem passar despercebidos.

Specificity = TN / TN + FP
#Tipo recall para valores negativos. #Quanto casos preditos como negativos o modelo é capaz de prever.

#Dado exemplo, a melhor métrica é o recall, visto que não queremos que uma pessoa infectada sai #na rua e infecte a população.

False positive Rate = FP/TN+FP
#Seria basicamente quantos valores negativos deixamos passar, ou seja, classificamos como positivo sendo que era negativo, em relação ao total de casos negativos na base.
Comentário resultado, do código:
O que quero mostrar é como funciona a métrica de precision(TP/(TP+FP)),nota-se que ao diminuirmos o nosso número de classes positivas há uma queda gradativa na precisão, visto que nosso FP(erro tipo 1) aumentou gradativamente, desse modo num target de 150k, nosso modelo conseguiu apenas acertar 48% dos casos que previu como positivo. Entretanto, ao olhar accuracy e sensibilidade(recall),nota-se que não temos uma diminuição significativa, visto que accuracy leva em conta todas as previsões(TP+TN/(TP+TN+FP+FN)) e o recall leva em conta apenas quanto dos casos positivos conseguimos captar no modelo. TP/(TP+FN), nota-se que o FN diminiui gradativamente. Portanto, nota-se para classes desbalanceadas a accuracy e recall podem ser perigosas métricas.Assim, é preciso aplicar métricas como ROC AUC. Nota-se que a acurácia do modelo pode nos enganar.Percebe-se que a média e mediana do salário nos

    
