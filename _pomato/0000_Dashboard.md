---

title: "Portfolio Management Tool"
# author: "Philipp Lang"
# is_post: true
permalink: /dashboard/
# categories: Portfolio_Risk
# tags: [Investing, Data, PortfolioManagement]
toc: false
# toc_label: "Table of Contents"
# toc_icon: "cog"
# toc_sticky: true
classes: wide

---

On the basis of a sample portfolio, this dashboard presents the results of all relevant analyses. Expect an optimized sample portfolio with each new analysis, as well as new graphics and tables.


**Disclaimer:** Please, for your own sake, DO NOT under any circumstances base your investment decisions on this research project. It is a purely academic project based on outdated data. Do your own research or consult an investment professional.


**Code**: If you are interested in the underlying mechanics of the analyses and data collection, please have a look at the jupyter notebooks on my [github repo](https://github.com/Mebbel/PortfolioManagement){:target="_blank"} and read through the other articles of this blog series.


## Overview

Sample portfolio composed of iShares Core Series with the intent of a global diversification. There are no further assumptions or restrictions applied to creating this portfolio, yet.

| ISIN            | Name                                            |  Weight  |
|:----------------|:------------------------------------------------|:--------:|
| IE00B4L5Y983    | iShares Core MSCI World UCITS ETF               |      20% |
| IE00B5BMR087    | iShares Core S&P 500 UCITS ETF USD (Acc)        |      20% |
| IE00BKM4GZ66    | iShares Core MSCI EM IMI UCITS ETF USD (Acc)    |      20% |
| IE00B53L3W79    | iShares Core EURO STOXX 50 UCITS ETF EUR (Acc)  |      20% |
| IE00B4L5YX21    | iShares Core MSCI Japan IMI UCITS ETF USD (Acc) |      20% |


### Value over time

Change in value of the portfolio over time, normalized to most current period. With the black line represting the closing prices of each trading day, and the red shadow indicating the daily spread between highest and lowest prices.

![Portfolio Value over Time](/assets/images/dashboard_portfolio_value_over_time.png){: style="text-align: center;"}

*Underlying assumption:* The portfolio was bought some time ago, s.t. the portfolio holdings have the specified portfolio weights today. 


### Diversification

Regional diversification of the portfolio holdings at a specific date. The portfolio seems reasonably diversified when looking at regions. Within regions, there is a very high concentration on companies from the USA and Japan. 

![Diversification by Region](/assets/images/dashboard_diversification_doughnut.png){: style="text-align: center;"}

*Underlying assumption:* The country corresponds to the headquarter of the company. It does not mean that it is also the country where most of the revenue/profit is created. 

*Comment*: The category "unknwon" is a mapping problem. This requires a better data quality process for mapping iShares holdings to an ISIN.