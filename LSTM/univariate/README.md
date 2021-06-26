# <center>Timeseries Dataset future prediction</center>
# <center>Univariate case LSTM vs Dense</center>

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


SingleStep, Multistep: 
This refers to the output chosen: 1 times in the future is told as single step.  Many times to be predicted in the future will be called MultiStep. We concentrate here in SingleStep. Moreover, as the output can be any temperature value this case is a **regression** not a classification problem. Accuracy will be measured with Rsquared (R2).

(in another notebook the multivariate multistep case is studied)


**The objective** is to predict the Temperature in 12 hours time, using the temperature data of the 120 hours just passed.


# RESULTS
- **LSTM 3x128** we try to reach the best performance possible from the start with a "big" LSTM network. R2 = 87.86%.
    Graphically the  estimation looks quite good. It is shown in 3 plots with 3000 samples each. The full test set has 13887 samples.
- **LSTM 1x32** we explore what would happen with a smaller network and surprisingly we get a slightly better result. R2 = 88.38%.
    To me this means the 1st network is oversized for this problem.
    Worth noting is that the first network needs a bigger batch to get optimal results (512) as opposed to the 2nd network that needs a smaller one (128)
- **Dense 3x128** we explore how much better the LSTM networks are compared to regular Dense networks. We can see that for the big network the result of Dense is similar or even better. R2 = 88.11%.
- **Dense 1x32** for the small network Dense is not performing as good as LSTM. R2 = 88.22%. Regardless of the R2 number, the prediction looks better looking at the plot though the number is similar.
- **ML conventional** finally we explore what would be the performance of conventional algorithms in timeseries prediction. 
    Performance is quite good to me in some cases. SVM regression reached 87.63% and Linear regression got a 87.2% in 1 minute training!!! 
    But we can clearly see that LSTM networks perform better when volume of data is starting to getting big.
