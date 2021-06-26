# <center>Hyperparameter Optimization in Neural Networks using Callbacks</center>
Dataset used: telecust.csv   -->as it seems a tough one

**Methods under study:**

1. [GRID with Loop](#id1)
2. [Sci-kit Learn GridSearchCV](#id2)
3. [Sci-kit Learn RandomizedSearchCV](#id3)
4. [Keras RandomSearch](#id4)
5. [Keras Hyperband](#id5)

Study and compare all 5 methods to optimise hyperparameters in a NN.
They are considered hyperparameters all that have an influence in the final result of accuracy prediction. 

It includes:
- Architecture parameters
    + [Number of layers](#id6)
    + [Number of neurons per layer](#id6) (all layers the same for the sake of complexity)
- Model training parameters
    + [Epochs](#id6)
    + [Batch size](#id6)
- Network functional parameters (the usual hyperparams)
    + [Entry layer activation function](#id6)
    + [Hidden layers activation functions](#id6)
    + [network optimiser (of cost function)](#id6) (it is usually a hyperparemeter but it has been fixed to Adam in this case)

Two **CALLBACKS** have been used to improve accuracy and accelerate the training process, as it can be really long in "brute force" cases 
1. Method [EarlyStopping](#id7) : to avoid overfit/variance
2. Method [ModelCheckpoint](#id7) : to save in disk the model with the best accuraacy in the fitting iteration

# CONCLUSIONS
- **GRID with loop** method is the one that finds the best model, though as it tests all combinations ("brute force") it takes a long time. It does not make K-fold CV and it uses the 20% part of the dataset for test, in order to validate models during the fitting iteration. Overfit is intended to be avoided not with CV but with the callbacks: EarlyStopping and ModelCheckPoint.
- **GridSearchCV** Sci-kit Learn method is using "brute force" as well, but it gets worse results. In my opinion, it is due to including a 5-fold CV. That means, that it takes another 20% of the training set to validate models, therefore, models get trained with only 64% of samples in the original dataset and results get worse.
- **RandomizedSearchCV** Sci-kit Learn method is a good trade-off between duration and performance. It is worth noting that exploring a bigger number of parameters sets does not improve the results. However, a 5-fold CV does improve the results achieved with a 3-fold CV. In my opinion, it is because models are trained with more data. 
- **RandomSearch** Keras method, is not very practical as it optimizes epochs and batch_size on its own. So, after you see what model and parameters are the best, you are missing the epochs and batch to be used. A new optimisation of those 2 parametrs is needed.
- **Hyperband** Keras method, surprisingly is as time consuming as "brute force" methods. It makes as many trials as hyperparameters combinations or even some more: 12 trials, 10 hiperp combs. It easily allows to include callbacks thanks to which the process is accelerated, but this is also the case in brute force methods, thus I see no advantage in using it.
