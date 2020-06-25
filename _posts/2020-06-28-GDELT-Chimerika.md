---
title: "Chimerika - China and USA Relations & Global News, Stocks and Currency"
date: 2020-06-28
tags: [China, USA,  Currency, Global News Media]
header:
  image: "/images/GDELT - Chimerika/Chimerika.jpg"
excerpt: "GDELT, News Media, Diplomacy"
mathjax: "true"
---

559 bn USD - official trade volume between China and USA in 2019, which accounts for ~5% of global trade volume (~20,000 bn).
Trade wars are reflected in the global media news:

 ![alt]({{ site.url }}{{ site.baseurl }}/images/\GDELT - Chimerika\plots_created\GDELT_sp500.png)

[GDELT](https://www.gdeltproject.org/) crawls news websites and systematically identifies and codifies entities and countries. Instruction getting data via .R API is described in my [previous post](https://zapkon.github.io/homepage/GDELT-Austria/.
We see that GDELT news volume has always a low around the New Year's Eve. The impact of COVID-19 is also clearly visible here:
In the Q1 the accusations and tension led to a double-peak of the volume of news. Also the S&P 500 dropped from it all time high.

 ![alt]({{ site.url }}{{ site.baseurl }}/images/\GDELT - Chimerika\plots_created\GDELT CYN_USD.png)
Here we see a weak negative relationship between the volume quantity of news and the strength of the USD relatively to the CYN.

[Quandl](https://www.quandl.com/) was used for getting the data [S&P 500 Inflation Adjusted by Month](https://www.quandl.com/data/MULTPL/SP500_INFLADJ_MONTH-S-P-500-Inflation-Adjusted-by-Month) and [Foreign Exchange Rate](https://www.quandl.com/data/SNB/DEVKUM-Foreign-Exchange-Rates). First sign up for free, get your key, and connect via .R API key!

```r
##### Get SP500 and FX data from Quandl ########
# Get your API key from quandl.com
quandl_api = "your_key"
Quandl.api_key(quandl_api)     # Add the key to the Quandl keychain

# Quandl.search(query="market index", silent=FALSE)

sp500 = Quandl("MULTPL/SP500_INFLADJ_MONTH", start_date = "2018-01-01", end_date = "2020-07-01")

currency = Quandl("SNB/DEVKUM", start_date = "2017-01-01", end_date = "2020-07-01") # get all pairs
currency = currency[,c(1,46)]                           # pick the pair CYN/USD
colnames(currency)[2] = "CNY_per_USD"
currency$CNY_per_USD = 1/currency$CNY_per_USD *100      # convert format for better interpretation
```



Happy Discovering!
