## Consideration of Decred's order books in comparison to other projects

Considering the market maker proposals currently under discussion, some of the big differences between proposals are in regard to the level of liquidity being offered and how far it would be positioned from the price (how tight the spread is).

I have collected order book data for DCR and a number of other cryptoassets, by pulling data from the public APIs of the exchanges every 15 minutes. The aim is to quantify how deep the DCR order books are now, how much of a difference the MM liquidity would make, and how this compares to the liquidity of other selected cryptoassets.

To process this data, I have aggregated the open orders which are 1 to 5% away from the current price, in either direction. In this aggregated data-set, at each snapshot you can see how much DCR (or other asset) was wanted in bids to buy, at -1%, -2%, -3%, -4%, -5% of the current price - and the same on the other side with asks to sell DCR at up to 1-5% over current price.

To enable comparisons between assets, I have converted them to USD equivalent (by manually entering the price on Aug 24, this is rough work).

Data collection has only been up and running for a few days (less for some exchanges/pairs), so this should be considered a preliminary analysis and over a longer timeframe the average liquidity for these pairs may be quite different. 

![Order book depth for a selection of assets](img/orderbook-depth.png)

The red line on the bar charts indicates $50k, which is the maximum amount of liquidity that would be provided per pair (by i2, at a 5% spread). Grapefruit is proposing $30k at 1-2% spread. You can see in the graph that this kind of additional availability would make a dramatic difference to the order books for DCR. Other assets considered here have mostly already got that level of availability, on both sides and usually within 1% of the price. The sell side on DCR markets looks particularly weak over this short observation period.

XTZ also has relatively light order books, particularly on the sell side. This may be a reflection of the fact that (delegated) staking is available to Tezos holders and they can earn a share of rewards for doing so. 

DCR's order books for some markets are barely visible on this graph (there are also some where it's not listed), so here's a DCR only version:

![Order book depth for DCR](img/orderbook-depth-DCR.png)

DCR has the smallest market cap of the considered assets, so it is not reasonable to make a straight comparison with their order books. To make a fairer comparison, I have expressed the order book values as a percentage of the asset's total market cap.

![Order book depth for a selection of assets - expressed as % of market cap](img/orderbook-depth-mcap.png)

DCR order books still look thin relative to other assets, but after taking market cap into account the disparity is not as great.

The table below shows the mean observed size of orders up to 5% from the current price on each side (-5% is buy side). If you wanted or were willing to move the price by 5% to get (rid of) some of the asset, this is how much you would need (in USD). The formatting is rough because it's dumped directly from a script, but this allows it to be easily updated (the [csv file]() this is based on is more likely to be updated).

| Pair    | binance_-5 | binance_5 | bitfinex_-5 | bitfinex_5 | bittrex_-5 | bittrex_5 | huobi_-5 | huobi_5 | kraken_-5 | kraken_5 |
| ------- | ---------: | --------: | ----------: | ---------: | ---------: | --------: | -------: | ------: | --------: | -------: |
| ADABTC  |     409000 |    270000 |          NA |         NA |     203000 |     98400 |   165000 |   93100 |    101000 |    34000 |
| ADAUSD  |     329000 |    139000 |          NA |         NA |      44100 |     30100 |   115000 |   76200 |    106000 |    82600 |
| DASHBTC |     138000 |     85500 |      338000 |     364000 |     141000 |     88900 |   193000 |  103000 |     84500 |    31800 |
| DASHUSD |      49400 |     27900 |      376000 |     385000 |         NA |        NA |   186000 |  154000 |     42500 |    73000 |
| DCRBTC  |      36100 |     23800 |          NA |         NA |      50500 |     20000 |    20300 |    5710 |        NA |       NA |
| DCRUSD  |         NA |        NA |          NA |         NA |         NA |        NA |    15600 |    6690 |        NA |       NA |
| EOSBTC  |     340000 |    265000 |      979000 |     887000 |      63600 |     34600 |   434000 |  220000 |    177000 |   129000 |
| EOSUSD  |     344000 |    264000 |     1540000 |    1500000 |      23100 |     16200 |   345000 |  282000 |    217000 |   234000 |
| LTCBTC  |     795000 |   1340000 |     1030000 |    1020000 |     292000 |    122000 |   305000 |  249000 |    233000 |   143000 |
| LTCUSD  |     495000 |    385000 |      907000 |    1100000 |     107000 |     83000 |   957000 |  680000 |    349000 |   329000 |
| XMRBTC  |     466000 |    303000 |      757000 |     694000 |     161000 |     94200 |   189000 |  139000 |    260000 |   219000 |
| XMRUSD  |      92700 |     70100 |      674000 |     622000 |         NA |        NA |   188000 |  123000 |    233000 |   206000 |
| XTZBTC  |         NA |        NA |       96600 |      66300 |         NA |        NA |    25700 |   17800 |    139000 |    69200 |
| XTZUSD  |         NA |        NA |       76300 |      74200 |         NA |        NA |    26300 |    3180 |     71100 |    52400 |
| ZECBTC  |     141000 |    107000 |      140000 |     124000 |      89400 |     64500 |   180000 |   95500 |     63400 |    25000 |
| ZECUSD  |      70600 |     34300 |      416000 |     402000 |      20500 |     13700 |   258000 |  112000 |     71700 |    62600 |

For DCR there are typically more orders on the buy side ($36k at Binance, $50k at Bittrex, $36k at Huobi across both BTC and USD pairs) than the sell side ($24k Binance, $20k Bittrex, $13k Huobi).

### Fluctuations in order book depth over time

This section is about establishing whether order book depth is relatively stable or not, and  deciding what an appropriate delay is between data snapshots. 

![Order book depth over time (5% from price)](img/DCR-orderbooks-time.png)

The lines show how the size of orders on the books (in USD) on each side, data recorded at 15 minute intervals. The sell side varies quite significantly over this observation period, between $10k and $30k at Bittrex, $10k-$20k at Binance, and steadily under $10k at Huobi, except for short periods where more DCR appears for sale.

I have produced equivalent graphs for all of the assets being tracked, they are in this [folder](img/) (and at the end of this document).

I'm planning to drop the temporal resolution to hourly snapshots and leave some version of these scripts running longer term.

The raw data is in a MySQL database and too large to share easily, but if you want access let me know and I can set you up. The aggregated data-set is [here](data/orderbook-observations-long.csv).

![Order book depth over time (5% from price)](img/ADA-orderbooks-time.png)
![Order book depth over time (5% from price)](img/DASH-orderbooks-time.png)
![Order book depth over time (5% from price)](img/EOS-orderbooks-time.png)
![Order book depth over time (5% from price)](img/LTC-orderbooks-time.png)
![Order book depth over time (5% from price)](img/XMR-orderbooks-time.png)
![Order book depth over time (5% from price)](img/XTZ-orderbooks-time.png)
![Order book depth over time (5% from price)](img/ZEC-orderbooks-time.png)
