# Datasheet Template

## Motivation

This dataset was created for use in data science and machine learning problems on Kaggle. It was created by Martin Søgaard Nielsen.

## Composition

### Content

The dataset contains roughly 12 days of limit order book data for Bitcoin (BTC), Ethereum (ETH) and Cardano (ADA).

The data contains information for the 15 best bid / ask price levels in the order book.

### Features

midpoint = the midpoint between the best bid and the best ask
spread = the difference between the best bid and the best ask

bids_distance_x = the distance of bid level x from the midprice in %
asks_distance_x = the distance of ask level x from the midprice in %

bids_market_notional_x = volume of market orders at bid level x
bids_limit_notional_x = volume of limit orders at bid level x
bids_cancel_notional_x = volume of canceled orders at bid level x

asks_market_notional_x = volume of market orders at ask level x
asks_limit_notional_x = volume of limit orders at ask level x
asks_cancel_notional_x = volume of canceled orders at ask level x

## Collection process

The dataset was created from raw order book messaged acquired by subscribing to the websocket of coinbase.com. The order books where then aggregated to construct snapshots of the limit order book at frequencies of 1 second, 1 minute and 5 minutes.

## Preprocessing/cleaning/labelling

The data were aggregated into 5-minute buckets.
 
## Uses

This dataset can be used for any number of tasks relating to historical order book modelling or systematic trading. The model data are not live and so they may be used theoretically but not for live trading.

## Distribution

The dataset is covered under a CC0: Public Domain license

## Maintenance

The dataset is not expected to be updated.
