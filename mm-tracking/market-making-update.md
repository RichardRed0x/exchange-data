This report considers the DCR order books and market dynamics since the start of market making activities by i2 Trading. 

See this previous report for background on order book data collection and comparison with other projects.

This analysis is based on the publicly available order book data, collected through the APIs of the various exchanges. One of the main objectives was to compare the order books before and after the market making activities began, to ensure that the service is being provided as described and see how it is affecting the markets.

![DCR order book depth at 5% over/under current price](/DCR-orderbooks-time-Oct15.png)

This graph shows the impact of i2's activities on the order books (starting Oct 22). The lines represent the amount available to buy and sell within 5% of the current price, and indeed you can see that around $50k of additional liquidity appeared and has been maintained most of the time since then. The graph also shows that there were some times where the target level of liquidity was not available. This is to be expected to some degree, and the proposal itself promised 90% uptime, aside from exchange outages.

This data represents all of the orders on the books, not just i2's, so while it is possible to know whether the target level of liquidity was present at a specific point in time it is not possible to know whether it was being provided by i2 or another party. 

| exchange | side/depth   | % on target |
| -------- | ------------ | ----------- |
| Binance  | Buy side 2%  | 73%         |
|          | Buy side 4%  | 79%         |
|          | Sell side 2% | 59%         |
|          | Sell side 4% | 84%         |
| Bittrex  | Buy side 2%  | 88%         |
|          | Buy side 4%  | 92%         |
|          | Sell side 2% | 43%         |
|          | Sell side 4% | 84%         |
| Huobi    | Buy side 2%  | 52%         |
|          | Buy side 4%  | 60%         |
|          | Sell side 2% | 43%         |
|          | Sell side 4% | 69%         |

These tables are based on data from Oct 22 to Nov 15, DCR/BTC on Binance, Bittrex and Huobi, and DCRUSDT on Huobi (Bittrex USDT market was added during the observation period but is not considered here). The requirements considered were to have 3 BTC or $30k available within 2%, and 5BTC or $50k available at 4%. The price in each hour was used to set the target amount of DCR which should be available, the table shows the percentage of observations where the target levels of liquidity were available.

Looking at the data at each observation point suggests that the target level of liquidity was available less than half of the time on some exchanges/pairs. In particular the tight sell side orders on Bittrex were only sufficiently there on 43% of observations, this was also the weakest measure on Binance (59%). Uptime on Huobi seems to have been generally not great. 

What these figures don't show is whether the target was missed by a little or a lot. It is possible there are many observations where there was just a little less DCR than the target because a big trade just happened. The next graph shows a breakdown of how far over/under the available liquidity was at each observation, as compared to the target for that hour.

![](liquidity-targets.png)

Looking at the sell side 2% target, it is clear that on many observations the order books had around 80-90% of the target liquidity. There are other observations where very little liquidity was available, when presumably i2 were not active in making the market - these are identified by the cluster of bars near 0, representing the state of the order books when i2 are offline.

It is also interesting to consider why the order books got thin at certain points in time, and the degree to which the liquidity provision was available during periods of price volatility. The graph below shows order book depth at the +/- 5% level (top), history of filled orders on 3 pairs (middle), and volume traded per hour  (bottom).![Order books, completed orders, volume per hour](/orderbooks-history-volume.png)

There does seem to be a relationship between price movement and market making down time, with significant moves up in price being followed by a period of low availability on the sell side (perhaps as i2 have to re-fill the exchange account, if they sold a lot of the DCR they held there).











