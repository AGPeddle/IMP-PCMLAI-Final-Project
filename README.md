# Estimating the Depth of the Order Book


## NON-TECHNICAL EXPLANATION OF YOUR PROJECT
Most financial markets run what is called a Limit Order Book, where there are at any time any number of orders to be filled when a price rises or falls to a given limit. There are also so-called Market Orders entering the market at any time which are matched at the best price. Understanding the distribution of orders below the top level of the book is vital to understanding the available liquidity and the costs which will be incurred to trade.

The aim of this project is to predict the characteristics for the limit order book from easily-observable quantities in the market like the price history and the bid-ask spread. It does this by using a neural network which has been fit against observed data.

## DATA
The data which were used to train the model are order book data for Bitcoin at 5 minute intervals, taken from here: https://www.kaggle.com/datasets/martinsn/high-frequency-crypto-limit-order-book-data. They cover roughly 12 days and have observed prices, spreads, volumes, and details of the order book.

## MODEL 
The model is a neural net model with an initial convolutional layer to smooth the prices, spreads, and volumes over time. These timeseries data are the features of the model. After the convolution layer there are a series of LSTM layers with hidden state, which is an approach that has been taken in timeseries analysis before. The output targets of the model are the weighted distances, i.e. the distance from the midpoint multiplied by the volume at that point, for the first five levels on either side of the midpoint.

## HYPERPARAMETER OPTIMSATION
The hyperparameters of this model are the kernel length of the convolution layer, the number of samples of lookback to include in the timeseries, and the number of hidden nodes and hidden layers of the LSTM layer. They were optimised by Bayesian optimisation with an RBF kernel for the Gaussian process surrogate function and taking expected improvement as the acquisition function.

## RESULTS
The model does a poor job of resolving the actual levels in question, but this is not surprising given that all known models also struggle with this. What the model does manage to do quite well is to resolve the dynamics of the order book and the way in which the relative depth on both sides of the midpoint evolve in response to market events.
