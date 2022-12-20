# trading_algo

Universe:
1) Get list of US Chinese stocks from Refinitive, store in US Chinese Stocks.csv
2) Filter list for ADRs and valid market cap data
3) What's left is stored in 'valid_stocks'

Strategy:
1) Pull pre-market data from Yahoo Fianance
    4am to 9:30am 
    --> ln(9:29am price / 4am price) is "premarket"
    Do this for each stock on the ticker
    now have "premarket return" for everything on the list.
2) Apply filters to premarket; e.g., <= -5%
    --> if it satisfies this filter, it's a BUY because the assumption is the market will overreact in the first hour, but will then mean-revert later in the day or maybe the next day.
    --> it's a fixed amount of shares for each.
    so, trade execution:
      1. if(filter satisfied): market order to BUY x shares of stock at open.
      2. IMMEDIATELY issue a limit order to SELL x shares at price open*(1+alpha) where alpha is some % 
3) 
