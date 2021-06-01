# Comparativa Algoritmos de Clasificación
En lenguaje Python con el entorno Jupiter Notebooks

**Algoritmos usados en Clasificación**   
1. [KNN](#id1)
2. [Arbol de decisión](#id2)
3. [SVM](#id3)
4. [Regresión Logística](#id4)
5. [Random Forest](#id5)
6. [XGBoost](#id6)

**Datasets de estudio**
- Medicamentos
- Células de cancer
- Clientes de operador Telecom
- Churn de operador Telecom
- Numeros escritos a mano: dataset MNIST 
  + 60.000 muestras entrenamiento
  + 10.000 muestras de test
  
**Resultados**
Medicamentos
  El mejor SVM (97,5%) luego Decision Tree y Random Forest
Células cancer
  El mejor es KNN (100%) luego el resto excepto LR que queda al final
Clientes Telecom
  El mejor es KNN (43%) seguido de Logistic Regression y SVM
Churn Telecom
  El mejor es XGBoost (87,5%) luego el resto excepto KNN que queda al final
Dataset MNIST
  El mejor es KNN
  No está nada mal comparado con lo que se consigue con una red neuronal
    Red 1 capa Dense 512 N -> 98,6%
    Red varias capas LeNet5: CNN 6 +Pooling +CNN 16 +Pooling +Dense 120 +Dense 84 -> 99,43%
    Ref: https://medium.com/analytics-vidhya/dense-or-convolutional-part-1-c75c59c5b4ad
    
