## finviz-api

[![PyPI version](https://badge.fury.io/py/finviz.svg)](https://badge.fury.io/py/finviz)
[![GitHub stars](https://img.shields.io/github/stars/mariostoev/finviz.svg)](https://github.com/mariostoev/finviz/stargazers)
[![Downloads](https://pepy.tech/badge/finviz)](https://pepy.tech/project/finviz)
[![HitCount](http://hits.dwyl.io/mariostoev/finviz.svg)](http://hits.dwyl.io/mariostoev/finviz)


`finviz` is compatible with Python 3.6+ only 

**What is Finviz?**

[Finviz.com](http://www.finviz.com) aims to make market information accessible and provides a lot of data in visual snapshots, allowing traders and investors to quickly find the stock, future or forex pair they are looking for. The site provides advanced screeners, market maps, analysis, comparative tools and charts.

### Important information

Any quotes data displayed on finviz.com is delayed by 15 minutes for NASDAQ, and 20 minutes for NYSE and AMEX. This API should **NOT** be used for live trading, it's main purpuse is financial analysis, research and data scraping.

### Install the current release using PyPi

    pip install finviz

### Using Screener()

    from finviz.screener import Screener
    
    filters = ['exch_nasd', 'idx_sp500']  # Shows companies in NASDAQ which are in the S&P500
    stock_list = Screener(filters=filters, order='price')  # Get the first 50 results sorted by price ascending
    
    # Export the screener results to .csv 
    stock_list.to_csv()
    
    # Create a SQLite database 
    stock_list.to_sqlite()
    
    for stock in stock_list[9:19]:  # Loop through 10th - 20th stocks 
        print(stock['Ticker'], stock['Price']) # Print symbol and price
    
    # Add more filters
    stock_list.add(filters=['fa_div_high'])  # Show stocks with high dividend yield
    # or just stock_list(filters=['fa_div_high'])
 
    # Print the table into the console
    print(stock_list)

![alt text](https://i.imgur.com/cb7UdxB.png)

### Download results as charts

    stock_list.get_charts(period='m', chart_type='c', size='l', ta=False)  # Monthly, Candles, Large, No Technical Analysis
    
    # period='d' > daily 
    # period='w' > weekly
    # period='m' > monthly
    
    # chart_type='c' > candle
    # chart_type='l' > lines
    
    # size='m' > small
    # size='l' > large
    
    # ta=True > display technical analysis
    # ta=False > ignore technical analysis

### Documentation

You can read the rest of the documentation inside the docstrings.

