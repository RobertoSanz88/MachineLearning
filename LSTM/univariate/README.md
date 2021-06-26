# <center>Timeseries Dataset future prediction </center>
# <center>Univariate case LSTM vs Dense </center>

Dataset used: "jena_climate_2009_2016.csv" for Temperature prediction

<a name="id8"></a>
**Studied configurations:**

1. [LSTM 3x128](#id1)
2. [LSTM 1x32](#id2)
3. [Dense 3x128](#id3)
4. [Dense 1x32](#id4)
5. [ML conventional](#id5)

The univariate case:
The mentioned dataset includes originally 14 features of weather forecast. We will concentrate in just one of them: one variable/feature.
(in another notebook the multivariate case is studied)

Time series with LSTM:
Time series are data coming from the same subject but taken at different times as opposed to other datasets where observations are coming from different subjects with the same features.
LSTM neural networks are used when data are time series and the target prediction is a time in the future.
Observations/samples need to be built taking into account time samples that will be used as input(x)  and time samples to be used as output(y). So, though there is only 1 feature, the input is 2D, (samples, 1 feature time history)

SingleStep, Multistep: This refers to the output chosen: 1 times in the future is told as single step
. Many times to be predicted in the future will be called MultiStep. We concentrate here in SingleStep.
(in another notebook the multivariate multistep case is studied)

**The objective** is to predict the Temperature in 12 hours time, using the temperature data of the 120 hours just passed.


# CONCLUSIONS
- **GRID with loop** method is the one that finds the best model, though as it tests all combinations ("brute force") it takes a long time. It does not make K-fold CV and it uses the 20% part of the dataset for test, in order to validate models during the fitting iteration. Overfit is intended to be avoided not with CV but with the callbacks: EarlyStopping and ModelCheckPoint.
- **GridSearchCV** Sci-kit Learn method is using "brute force" as well, but it gets worse results. In my opinion, it is due to including a 5-fold CV. That means, that it takes another 20% of the training set to validate models, therefore, models get trained with only 64% of samples in the original dataset and results get worse.
- **RandomizedSearchCV** Sci-kit Learn method is a good trade-off between duration and performance. It is worth noting that exploring a bigger number of parameters sets does not improve the results. However, a 5-fold CV does improve the results achieved with a 3-fold CV. In my opinion, it is because models are trained with more data. 
- **RandomSearch** Keras method, is not very practical as it optimizes epochs and batch_size on its own. So, after you see what model and parameters are the best, you are missing the epochs and batch to be used. A new optimisation of those 2 parametrs is needed.
- **Hyperband** Keras method, surprisingly is as time consuming as "brute force" methods. It makes as many trials as hyperparameters combinations or even some more: 12 trials, 10 hiperp combs. It easily allows to include callbacks thanks to which the process is accelerated, but this is also the case in brute force methods, thus I see no advantage in using it.
