---

title: "Uncovering hidden risks in ETF-Portfolios"
# author: "Philipp Lang"
# is_post: true
categories: Portfolio_Risk
tags: [Investing, Data, PortfolioManagement]
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
toc_sticky: true

---

Investing in public markets in a well-diversified manner to mitigate individual securities risk is getting easier and easier. With the help of ETF products, an investor can get exposure to hundreds of companies by buying a single security.

There is a large number of ETF products in the market to invest in different ideas, like investing in a specific index, a foreign market or a new trend.

With the investment in a basket of securities, there comes a promise of security. An investment in a market index like the S&P 500 is an investment in 500 of the best companies of the U.S. economy. With the MSCI World comes exposure to the largest publicly traded companies of all developed markets. And with the MSCI ACWI this is extended by investments in both developed and emerging markets.

With broad diversification the single security risk becomes less important, as the future of a whole economy of a country or group of countries becomes more important than the outlook of a single company.

Sounds like an almost fool-proof way of investing. But, is it really?


## Example of hidden risks

Following standard portfolio optimization principles, a typical ETF-portfolio will be broadly diversified and have low correlation across investments. 

To give an example for hidden risks, let us look at the most invested indexes with iShares ETFs:

* MSCI World
* S&P 500
* MSCI Emerging Markets


A portfolio setup with these ETFs promises a good level of diversification, when judged solely by the naming of the ETFs and their description. But an inspection of the actual investments easily identifies two key risks of ETFs w.r.t diversification in an ETF-Portfolio:

* Several products have an almost identical portfolio (MSCI World and S&P500)
* A substantial part of the index' value comes from a few, large companies

|-----------------+------------+-----------------+----------------|
| Top | MSCI World | | S&P 500 | | MSCI EM | |
|:------|:----------- | :---------: |:-------------| :---: | :-------|:-----:|
|1	|Apple        | 4,77%       | Apple        | 7,02% | TSMC    | 6,29% |
|2	|Microsoft    | 3,61%	    | Microsoft    | 5,94% | Tencent | 3,92% |
|3	|Alphabet A/C | 2,73%	    | Alphabet A/C | 4,21% | Samsung | 3,29% |
|4	|Amazon       | 2,43%	    | Amazon       | 3,63% | Alibaba | 2,60% |
|5	|Tesla        | 1,28%	    | Tesla        | 1,93% | Meituan | 1,33% |
|**Total** 	|         | **13,67%**	|              |**22,73%** |     | **17,43%**|

<font size = 1>(Data as of 13.02.2022; MSCI World = iShares MSCI World UCITS ETF; S&P500 = iShares Core S&P 500 UCITS ETF; MSCI EM = iShares Core MSCI EM IMI UCITS ETF) </font>

*Note:* Indices are usually weighted by market capitalization, which favours large corporations in many indices. When investment guidelines of different indices overlap, so will their exposure to large corporations.

Knowing and manging these risks can quickly become very time-consuming and complex. The portfolio weights change constantly with both market prices and the composition of indices. An example of large impact changes of indices was the inclusion of Tesla to the S&P500 index on 21.12.2020. Whereas Tesla was part of the MSCI World since 30.08.2013, with its growing market capitalization the effect on the S&P500 in 2020 was substantial.

For a passive investor who invests a portion of its savings in ETFs, this risk management task is too time-consuming and usually performed only a few times a year, if at all. Which means for many that they fly blind with their risks for long period of times.

For a passive investor with a savings accounts this level of risk management is incompatible with the available time and in many cases knowledge of financial markets and mathematics. Unfortunately that leads to blind-flight for many investors concerning the current risks of their portfolio.


## Outlook

Portfolio risks should be identifiable by everyone. This project revolves around making is easier for passive investors to uncover hidden portfolio risks. These include high exposure to single companies, countries or industries.   

