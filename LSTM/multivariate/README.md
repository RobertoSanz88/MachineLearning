# <center>Timeseries Dataset future prediction</center>
# <center>Multivariate Multistep case </center>

Dataset used: "jena_climate_2009_2016.csv" for Temperature prediction

<a name="id8"></a>
**Studied configurations:**

1. [LSTM 1x32](#id1)
2. [Dense 1x32](#id2)
3. [LSTM 3x128](#id3)

Multivariate => we forecast one feature in the future, by training with that feature observations in the past + other features observations in the past. In this case, temperature, pressure and humidity.

Multistep => we forecast not only 1 point in the future but all from now to that point. In this case, from 1h to 12h in the future.


**The objective** is to predict the Temperature in 1 hour time, 2 hours time, .., up to 12 hours time (multistep), using the temperature data of the 120 hours just passed, plus pressure and humidity data of the 120 h just passed (multivariate)


# RESULTS
- **LSTM 1x32** we try this first as it was the best performer for univariate with R2 = 87.86%. This time it improves it to 92,02%. Partially, becausse it is averaging the accuracy of al time steps, from 1h to 12h, not just the 12h mark. The improvement, graphically seen, is quite important. We see it in **2 different ways of visualization**.
- **Dense 1x32** we check the impact of multivariate in the Dense network and in this case it gets less than 1% better upto 89%, far away from the above result. 
    The difference with the LSTM here is significant
- **LSTM 3x128** finally we try with the bigger network as we could expect something better, as the input data is more complex now. But the deceiving result is that it does not improve the result of 1x32
