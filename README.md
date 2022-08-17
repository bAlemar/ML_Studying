# ML_Studying
## Meu estudos de Machine learning e coisas desse tipo
Primeiro tópico é ##Matrix Confusion## 
#Iremos ver como analisar uma matriz de confusão e como tomar cuidado com classes desbalanceadas.


##MATRIX CONFUSION##
Medir performance de modelos de classificação, ajuda a entender o desempenho de um classificador. 
Matriz N x N , composta pelos valores preditos e os verdadeiros valores.

#True Positive(TP): O valor preditivo é positivo e o valor real é positivo também 
#True Negative(TN): O valor preditivo é negativo e o valor real é negativo também 
#False Positive(FP) - Type 1 error: #Valor preditivo é positivo e o valor real,entranto é negativo 
#False Negative(FN) - Type 2 error: #Valor preditivo é negativo e o valo real,entreanto é positivo

#Contexto: # Para isso iremos tomar como exemplo uma Matrix de Correlação de um modelo de previsão # para pessoas doentes(classe positiva) ou não(classe negativa).

#Lembrando linhas: Predict , colunas: Real

[560,60]
[50,330]
#1o passo: #Identificar os valores: #TP = 560 ; TN = 330 ; #FP = 60 ; #FN = 50

#Accuracy = TP + TN / (TP + FP + TN + FN)

96%
#OBS : # Caso tivermos uma classe desbalanceada,ex: dataset: 947 targets negatives and only 3 targets positives #Ao calcular accuracy pensamos, nosso modelo tem 96% de 
acurácia em prever se as pessoas estão #doentes ou não... Entretanto, é exatamente ao contrário, 96% acurácia em prever pessoas não doentes. #Nesse contexto, devemos 
focar em prever os resultados positivos corretamente. #Desse modo iremos trabalhar com 2 novas métricas: Precision vs Recall.

==============//==============//==============//==============//==============//==============

Precision = TP / TP + FP #Quantos casos preditos como positivos, são realmente positivos 90%.Ou seja, 90% da previsão de casos positivos são realmente positivos. 
Precision é útil quando nossa preocupação maior é em cima dos falsos negativos, ou seja,valores que foram previstos como negativos quando na verdade eram positivos. 
#Por exemplo, num sistema de recomendação de música,e-commerce etc... devemos focar na Precision,visto que resultados errados podem levar a perde de clientes e 
prejudicar o negócio.

==============//==============//==============//==============//==============//==============

Recall/Sensitivy/TPR = TP / TP + FN
Quantos casos preditos como positivos o modelo é capaz de prever,ou seja,91% dos valores positivos são previstos pelo nosso modelo. 
Recall é útil quando Falso Negativo supera o Falso Positivo e principalmente quando não queremos nenhuma classe positiva "passar despercebida".
Por exemplo,casos médicos em que é irrelevante dispararmos um alarme falso, entretanto casos positivos não podem passar despercebidos.
Dado exemplo, a melhor métrica é o recall, visto que não queremos que uma pessoa infectada sai #na rua e infecte a população.

==============//==============//==============//==============//==============//==============

Specificity = TN / TN + FP
#Tipo recall para valores negativos. #Quanto casos preditos como negativos o modelo é capaz de prever.

==============//==============//==============//==============//==============//==============

False positive Rate = FP/TN+FP
#Seria basicamente quantos valores negativos deixamos passar, ou seja, classificamos como positivo sendo que era negativo, em relação ao total de casos negativos na 
base.

==============//==============//==============//==============//==============//==============
Comentário resultado, do código:
De início queria analisar como comporta as métricas de accuracy,recall e precision conforme ia desbalanceado as classes. Nesse sentido, nota-se que a métrica de 
precision, diminuiu gradativamente conforme foi diminuindo nossas classes positivas, visto que nosso FP(erro tipo 1) aumentou gradativamente e além disso a proporção 
entre TP e FP diminuiu. Desse modo, num target de 150k, nosso modelo conseguiu apenas acertar 48% dos casos que previu como positivo.
Entretanto, ao olhar accuracy e sensibilidade(recall),nota-se que não temos uma diminuição significativa, visto que accuracy leva em conta todas as 
previsões(TP+TN/(TP+TN+FP+FN)) e o recall leva em conta apenas quanto dos casos positivos conseguimos captar no modelo. TP/(TP+FN), nota-se que o FN diminiui 
gradativamente. Portanto, nota-se para classes desbalanceadas a accuracy e recall podem ser perigosas métricas.
Assim,  percebe-se que a accuracy não pode ser melhor métrica para avaliar a performance de modelos de classificação. Como solução, podemos utilizar a curva de ROC, a 
qual é um gráfico, o qual eixo x é a especificidade(FPR) e eixo y é a (TPR), dessa maneira nota-se que a uma maior área irá trazer a melhor modelo, uma vez que 
queremos maximizar o TPR enquanto minimizamos FPR.



    
