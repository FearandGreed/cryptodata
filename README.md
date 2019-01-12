# cryptoprice google sheet plugin

### what is it
a lighter and free alternative to the excellent [CryptoFinance](https://cryptofinance.ai) google sheet plugin to get all crypto data from the also excellent [CoinPaprika](https://coinpaprika.com/) API.

### how does it work
it pulls all tickers data into a single sheet (to ensure a fair use of the API), then a `CRYPTOPRICE("symbol", "data")` function allows you to pull specific data for ay coin.

### how to install
- open your favorite crypto spreadsheet, and create a sheet named `data`
- go to the menu `Tools > Script Editor`
- paste the content of the file `cryptoprice.gs` into the editor, then save
- go back to your spreadsheet, refresh the page
- you should now have a menu item called `CryptoPrice`. Click on it, then click on `Update`
- you can now use the plugin anywhere like this : `=CRYPTOPRICE("ETH", "btc_price")`

### how to use
- paste this in any cell : `=CRYPTOPRICE("ETH", "btc_price")` (you can discover the available data in the `data` sheet)

### update data
- first, click on the menu item `CryptoPrice`, then click on `Update` (will refresh raw data)
- to refresh your calls in other sheets, the best way i found is adding a dummy reference in the formula like this :

`=CRYPTOPRICE("ETH", "btc_price", $A$1)`

and updating the `$A$1` cell with whatever data.

Another way to find data with better performance (but poor readability) :

`=INDEX(data!$A$1:$Z; MATCH("ETH"; data!$C$1:$C; 0); MATCH("btc_price"; data!$A$1:$1; 0))`

### limitations
- can give you data in USD/BTC/ETH (according to what CoinPaprika is providing)
- won't give you any specific exchange data
- won't give you global market data like total marketcap (possible but not yet implemented)
- should respect CoinPaprika API fair use since it pull all data in one API call (rate limit is 10 reqs/s), but since request come from google's servers, i can't guarantee the fair use
- for now CoinPaprika's API is free, i can't guarantee it won't change
- performances are not great, but it does the job (remember, it's free)

### improve it
- i'm  welcoming issues, forks and PR, feel free to do better than what i did and if you do, share it !

### show some love
BTC : `389avCg3HYBBqnBX8S2PB2mvXPfGKx3cm4`
LTC : `LbaaxtsCeB9rt4EiXtFYwkZC9TnZtsvExt`
