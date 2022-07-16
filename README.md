# play-with-investpy

Just playing around with this library I discovered


<h3 align="center">Financial Data Extraction from Investing.com with Python</h3>

investpy is a Python package to retrieve data from [Investing.com](https://www.investing.com/), which provides data retrieval 
from up to 39952 stocks, 82221 funds, 11403 ETFs, 2029 currency crosses, 7797 indices, 688 bonds, 66 commodities, 250 certificates, 
and 4697 cryptocurrencies.

investpy allows the user to download both recent and historical data from all the financial products indexed at Investing.com. 
**It includes data from all over the world**, from countries such as United States, France, India, Spain, Russia, or Germany, 
amongst many others.

investpy seeks to be one of the most complete Python packages when it comes to financial data extraction to stop relying 
on public/private APIs since investpy is **FREE** and has **NO LIMITATIONS**. These are some of the features that currently lead 
investpy to be one of the most consistent packages when it comes to financial data retrieval.

[![Python Version](https://img.shields.io/pypi/pyversions/investpy.svg)](https://pypi.org/project/investpy/)
[![PyPI Version](https://img.shields.io/pypi/v/investpy.svg)](https://pypi.org/project/investpy/)
[![Package Status](https://img.shields.io/pypi/status/investpy.svg)](https://pypi.org/project/investpy/)
[![Documentation Status](https://readthedocs.org/projects/investpy/badge/?version=latest)](https://investpy.readthedocs.io/)


---

## :hammer_and_wrench: Installation

To get this package working you will need to **install it via pip** (with a Python 3.6 version or higher) on the terminal by typing:

``$ pip install investpy``

---

### :chart_with_upwards_trend: Recent/Historical Data Retrieval

investpy allows the user to **download both recent and historical data from any financial product indexed** 
(stocks, funds, ETFs, currency crosses, certificates, bonds, commodities, indices, and cryptos). In 
the example presented below, the historical data from the past years of a stock is retrieved. 

```python
import investpy

df = investpy.get_stock_historical_data(stock='AAPL',
                                        country='United States',
                                        from_date='01/01/2010',
                                        to_date='01/01/2020')
print(df.head())
```
```{r, engine='python', count_lines}
             Open   High    Low  Close     Volume Currency
Date                                                      
2010-01-04  30.49  30.64  30.34  30.57  123432176      USD
2010-01-05  30.66  30.80  30.46  30.63  150476160      USD
2010-01-06  30.63  30.75  30.11  30.14  138039728      USD
2010-01-07  30.25  30.29  29.86  30.08  119282440      USD
2010-01-08  30.04  30.29  29.87  30.28  111969192      USD
```

To get to know all the available recent and historical data extraction functions provided by 
investpy, and also, parameter tuning, please read the docs.

### :mag: Search Live Data

**Investing.com search engine is completely integrated** with investpy, which means that any available 
financial product (quote) can be easily found. The search function allows the user to tune the parameters 
to adjust the search results to their needs, where both product types and countries from where the 
products are, can be specified. **All the search functionality can be easily used**, for example, as 
presented in the following piece of code:

```python
import investpy

search_result = investpy.search_quotes(text='apple', products=['stocks'],
                                       countries=['united states'], n_results=1)
print(search_result)
```
```json
{"id_": 6408, "name": "Apple Inc", "symbol": "AAPL", "country": "united states", "tag": "/equities/apple-computer-inc", "pair_type": "stocks", "exchange": "NASDAQ"}
```

Retrieved search results will be a `list` of `investpy.utils.search_obj.SearchObj` class instances, unless
`n_results` is set to 1, when just a single `investpy.utils.search_obj.SearchObj` class instance will be returned.
To get to know which are the available functions and attributes of the returned search results, please read the related 
documentation at [Search Engine Documentation](https://investpy.readthedocs.io/search_api.html). So on, those 
search results let the user retrieve both recent and historical data, its information, the technical indicators,
the default currency, etc., as presented in the piece of code below:

```python
recent_data = search_result.retrieve_recent_data()
historical_data = search_result.retrieve_historical_data(from_date='01/01/2019', to_date='01/01/2020')
information = search_result.retrieve_information()
default_currency = search_result.retrieve_currency()
technical_indicators = search_result.retrieve_technical_indicators(interval='daily')
```

### :money_with_wings: Crypto Currencies Data Retrieval

Cryptocurrencies support has recently been included, to let the user retrieve data and information from any 
available crypto at Investing.com. Please note that some cryptocurrencies do not have available data indexed 
at Investing.com so that it can not be retrieved using investpy either, even though they are just a few, 
consider it.

As already presented previously, **historical data retrieval using investpy is really easy**. The piece of code 
presented below shows how to retrieve the past years of historical data from Bitcoin (BTC).

```python
import investpy

data = investpy.get_crypto_historical_data(crypto='bitcoin',
                                           from_date='01/01/2014',
                                           to_date='01/01/2019')

print(data.head())
```
```{r, engine='python', count_lines}
             Open    High    Low   Close  Volume Currency
Date                                                     
2014-01-01  805.9   829.9  771.0   815.9   10757      USD
2014-01-02  815.9   886.2  810.5   856.9   12812      USD
2014-01-03  856.9   888.2  839.4   884.3    9709      USD
2014-01-04  884.3   932.2  848.3   924.7   14239      USD
2014-01-05  924.7  1029.9  911.4  1014.7   21374      USD
```

---

## :open_book: Documentation

You can find the **complete investpy documentation** at [Documentation](https://investpy.readthedocs.io/).

---

## :card_index_dividers: Related projects

Since investpy is intended to retrieve data from different financial products as indexed in Investing.com, 
the **development of some support modules which implement an additional functionality based on investpy data**, 
is presented. Note that **anyone can contribute to this section** by creating any package, module, or utility that 
uses investpy. So on, the ones already created are going to be presented, since they are intended to be used 
combined with investpy:

- [pyrtfolio](https://github.com/alvarobartt/pyrtfolio/): is a Python package to generate stock portfolios.
- [trendet](https://github.com/alvarobartt/trendet/): is a Python package for trend detection on stock time-series data.
- [pypme](https://github.com/ymyke/pypme): is a Python package for PME (Public Market Equivalent) calculation

If you developed an interesting/useful project based on investpy data, please open an issue to let me know to 
include it in this section.

---

