# Comparativa Redes Neuronales

**Redes usadas**   
- Red Dense 1 capa oculta
- Red Dense de 3 capas ocultas 

**Datasets usados**   
- Medicamentos

**Resultados**
- Medicamentos
	+ Con 1 capa: con 8 neuronas ya alcanzo la precisión de 97,5% de SVM que era el mejor de los tradicionales
        + Aunque suba el número de neuronas, ej 512, no aumenta la precisión
	+ Con 3 capas: con 32 neuronas si puedo superarlo y llegar al 100%. 
        + Más capas y más neuronas sí generan más inteligencia, que los sistemas tradicionales
        + Pero 3 capas de 8 neuronas predicen peor que 1 capa de 8 neuronas. 
        	- Parece que más inteligencia necesita además de más profundidad (capas) más neuronas por capa. 
- Clientes telecom
	+ Este es el que menos precisión he conseguido, 43% parece un dataset complicado de clasificar
	+ Con 1 NN de 1 capa y 8 neuronas ya consigo algo mejor precisión 46.5%
	+ Con 3 capas de 32 neuronas se consigue un 49%, mi máximo
	+ Con 5 capas de 63 neuronas se consigue peor precisión, por lo cual creo que ya el modelo está sobredimensionado y hace overfit
