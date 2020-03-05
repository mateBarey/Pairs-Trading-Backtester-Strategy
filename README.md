# Pairs-Trading-Backtester-Strategy

This Pairs Trading Backtester model works by using numpy pandas, statsmodels and matplotlib.

The algorithm first starts with an array of commodities you want to trade, for this example I used Cryptocurrency trading pairs

ETH,BTC, BAT, LTC, XMR, and BCH. 

The principle for pairs trading is finding cointegrated pairs of commodities/securities in similar markets but that diverge 

from time to time due to supply deman changes, buy/sell orders and news about a commodity. 

When there is a temporary divergence between two pairs one security/commodity moves opposite the other. The pairs trade would b

be to short the outperforming security/commodity  while going long on the underperforming  one; betting that the spread between

both instruments would soon converge.


Once I get the history of each commodity/security I can check if there is cointegration from any two instruments.

Cointegration is a different form of correlation. If 2 items are cointegrated the ratio between them will vary around a mean.

For pairs trading to work, the expected value of the ratio over time must converge to the mean. 


The algorithm uses statsmodels pvalue to check for cointegration between pairs. In general a p value < .05  Once I check each 

pair cointegration through a heat map with. The only problem when comparing many items is being subject to multiple 

comparison bias. So in general an extra step should be taken to ensure cointegration which is not done in this algo.


Once the cointegrated pair is found the ratio of both items is plotted to ensure it does generally vary around a mean.

The ratios are then separated for train and testing and we look at the zscore of a long term and short term moving average.

The algorithm is trained to short when the zscore is > 1 and long when < 1 and clear positions if the z score is between -.5 

0.5 . Once the Training set is proven to be profitable a optimal moving average window length can be found 

assuming a second window constant. The window length is found using the function created before to trade and iterating for 

the maximum argument in the training data. This is done also for the test data. Then the Returns vs window length is plotted

for  both train and test sets to visualize both optimal window lengths for both sets of data.
