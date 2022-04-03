# Challenge14

## Models

### Baseline

As a baseline for this project we use a trading strategy based on support vector machine algorithm, in which we use the rolling window data to generate the signal.
As a first solution we develop a SVM algorithm that takes as input features two rolling windows: a fast one with period of 4 and a slow one with period of 100.
We split the dataset into training and testing, each having three months of data, and we scale them.
After fitting the model on the training dataset, we make predictions on the training and testing data.
We see that our model performs well on the training, especially when it has to predict the buy signals, but doesn't perform well on the testing data, since our predictions will be always buy signals. Hence the cumulative return of the strategy and the actual cumulative returns will be overlapped. And since the trading period is bearish, by always buying we will be losing money.

![Cumulative Returns](./Resources/bokeh_plot.png)

### Tuned model

Since we have a lot of data but we used just few of them, we try by increasing the training period to one year. We adjust also the rolling windows, since 4 and 100 may be too far apart. By getting them closer we may end up with a more sensitive signal generation.
After training we test the strategy and we can see that the issue of detecting buy signals only still persists.
In this case the algorithm is making money since we took 3 different months for the testing, but only because we are in a bullish local trend.

![Cumulative Returns Tuned](./Resources/bokeh_plot (1).png)

### Different algorithm

We keep the same parameters: rolling window (period 4), rolling window (period 30), training size 12 months, testing size 3 months.
The new classifier we'll be using is the Logistic Regression, from the sklearn.linear module. In this case we have a model that like before predicts just buy signals and hence we end up with the same testing performance as before.

![Cumulative Returns Tuned](./Resources/bokeh_plot (2).png)

To conclude we can say that due to the complexity of the data at hand, it is required to use a more complex classifier able to detect hidden patterns in the data at hand.