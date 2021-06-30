# Neural Networks Comparison

**Networks used**   
- NN with 1 Dense hidden layer
- NN with 3 Dense hidden layers 

**Datasets used**   
- Drugs
- Telecom Customers

**Results**
- Drugs
	+ 1 layer with 8 neurons is enough to reach 97,5% accuracy that was the one achieved by SVM, the best of conventional ML methods.
        + Regardless the number of neurons is increased, eg to 512, accuracy does not improve.
	+ 3 layers with 32 neurons is needed to go beyond and reach even 100%. 
        + As conclusion, more layers and more neurons do generate more intelligence than conventional algorithms.
        + As highlight to remark that 3 layers with 8 neurons predict worse that 1 layer with 8 neurons.
        	- So it seems that more intelligence needs from, not only more layers, but also more neurons in each of those layers. 
- Telecom Customers
	+ Only a 43% accuracy was reached so it seems a difficult set for classification
	+ 1 layer with 8 neurons gets slightly better accuracy: 46.5%
	+ 3 layers with 32 neurons reaches 49%, the maximum
	+ 5 layers with 64 neurons gets worse accuracy, thus, I believe the model is oversized and is overfitting.
