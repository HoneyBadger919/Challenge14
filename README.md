# Challenge14

## Models

### Baseline

As a baseline for this project we use a momentum trading strategy based on the percentage-wise variation of the data during the period separating two subsequent records in our dataset. We will establish the strategy by imposing a trading signal to buy when the actual return is equal or greater than zero (price increasing), and a signal to sell when the actual returns is negative (price decreasing).
We then generate the strategy returns by shifting in time the trading signal and multiply it by the price variation: this because the signal whether to buy or sell on a certain day is based on what happened the day before.

After the plot we generate a better trading strategy based on support vector machine algorithm, in which we use the rolling window data to generate the signal.
We need to generate the features, which will be the fast and slow moving averages, shifted into the future since we need to anticipate through our analysis which direction the market will take in the next period.


