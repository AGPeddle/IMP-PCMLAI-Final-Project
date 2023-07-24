# Model Card

## Model Description

**Input:** The inputs of the model are the mid prices, spread between bid and ask, and volumes traded over the last 5 minutes. An ensemble of these 5-minute bars is used to give an impression of the trend and how moves in the market play into the order book.

**Output:** The output of the model is a set of predictions for the weighted distance of the top 5 levels on both bid and ask in the order book. Weighted means it is the distance from the current mid in percentage terms, multiplied by the total nominal available at that level.

**Model Architecture:** The model is a combination of a convolutional and LSTM neural network. The intial convolutional layer is designed to smooth out the noise inherent in the timeseries, while the LSTM layers beyond it aim to learn and capture autoregressive effects. The model is written in PyTorch and the hyperparameters have been optimised via Bayesian optimisation.

## Performance

Give a summary graph or metrics of how the model performs. Remember to include how you are measuring the performance and what data you analysed it on. 

## Limitations

The main limitation of the model is that while it captures the broad strokes of the market dynamics well, it is unable to model price levels in detail. Rather it indicates trends.

## Trade-offs

The main trade-off in developing the model is that it uses 5-minute bars for the intraday data. Using higher frequency of data would be interesting, indeed such data are available, but it becomes prohibitively expensive to train, test, and optimise the model in that case.
