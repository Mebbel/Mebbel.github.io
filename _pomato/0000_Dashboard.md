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

<style>
 /* Three image containers (use 25% for four, and 50% for two, etc) */
.column {
  float: left;
  width: 50%;
  padding: 10px;
}

/* Clear floats after image containers */
.row::after {
  content: "";
  clear: both;
  display: table;
} 

.column_33pc {
  float: left;
  width: 33%;
  padding: 10px;
}

#txbox{
    float: left;
    border: 1px solid black;
    box-shadow: 1px 2px 2px black;
    width: 100%;
    height: auto;
    padding-left: 5%;
    /* position: absolute; */
    border-radius: 25px;
  }

/* Table column alignments */
.col1-right td:nth-child(1) {text-align: right}
.col2-right td:nth-child(2) {text-align: right}
.col3-right td:nth-child(3) {text-align: right}
.col4-right td:nth-child(4) {text-align: right}
.col5-right td:nth-child(5) {text-align: right}
.col6-right td:nth-child(6) {text-align: right}
.col7-right td:nth-child(7) {text-align: right}

.col1-left td:nth-child(1) {text-align: left}
.col2-left td:nth-child(2) {text-align: left}
.col3-left td:nth-child(3) {text-align: left}
.col4-left td:nth-child(4) {text-align: left}
.col5-left td:nth-child(5) {text-align: left}
.col6-left td:nth-child(6) {text-align: left}
.col7-left td:nth-child(7) {text-align: left}

.col1-center td:nth-child(1) {text-align: center}
.col2-center td:nth-child(2) {text-align: center}
.col3-center td:nth-child(3) {text-align: center}
.col4-center td:nth-child(4) {text-align: center}
.col5-center td:nth-child(5) {text-align: center}
.col6-center td:nth-child(6) {text-align: center}
.col7-center td:nth-child(7) {text-align: center}

</style>


On the basis of a sample portfolio, this dashboard presents the results of all relevant analyses. Expect an optimized sample portfolio with each new analysis, as well as new graphics and tables.


<i class="fa fa-exclamation-circle"></i> **Disclaimer** Please, for your own sake, DO NOT under any circumstances base your investment decisions on this research project. It is a purely academic project based on outdated data. Do your own research or consult an investment professional.


<i class="fa fa-code"></i> **Code**: If you are interested in the underlying mechanics of the analyses and data collection, please have a look at the jupyter notebooks on my [github repo](https://github.com/Mebbel/PortfolioManagement){:target="_blank"} and read through the other articles of this blog series.


## Overview

Sample portfolio composed of iShares Core Series with the intent of a global diversification. There are no further assumptions or restrictions applied to creating this portfolio, yet.

*Assumptions:*
* 100.000€ Cash available for investments
* Transaction Costs according to Consorsbank model (see code for details)


\
*Stats* 
<div class="row">
<div class="column_33pc">
<div id="txbox" style='background-color:rgb(0,0,50); color:white; text-align:center'> Portfolio Value <br> 99,633€  </div>
</div>
<div class="column_33pc"> 
<div id="txbox" style='background-color:rgb(0,0,50); color:white; text-align:center'> Transaction Costs <br> 274€ </div>
</div>
<div class="column_33pc"> 
<div id="txbox" style='background-color:rgb(0,0,50); color:white; text-align:center'> Remaining Cash <br> 93€ </div>
</div>
</div> 


\
\
*Portfolio*

<table class='col1-left col2-left col3-center col4-right col5-right col6-right col7-right' width='100%'>
  <thead>
    <tr style="background-color:rgb(0,0,50); color:white;border-bottom:2px solid black">
      <th style='text-align:left'>ISIN</th>
      <th style='text-align:left'>Name</th>
      <th style='text-align:center'>Acc / Dist</th>
      <th style='text-align:center'>N</th>
      <th style='text-align:left'>Value</th>
      <th style='text-align:left'>Dist Last 12M</th>
      <th style='text-align:left'>Dist in %</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>IE00B4L5Y983</td>
      <td>iShares Core MSCI World UCITS ETF</td>
      <td>Acc</td>
      <td>283</td>
      <td>19,913</td>
      <td>-</td>
      <td>-</td>
    </tr>
    <tr>
      <td>IE0031442068</td>
      <td>iShares Core S&amp;P 500 UCITS ETF USD (Dist)</td>
      <td>Dist</td>
      <td>531</td>
      <td>19,912</td>
      <td>231</td>
      <td>1.16</td>
    </tr>
    <tr>
      <td>IE00BKM4GZ66</td>
      <td>iShares Core MSCI EM IMI UCITS ETF USD (Acc)</td>
      <td>Acc</td>
      <td>721</td>
      <td>19,928</td>
      <td>-</td>
      <td>-</td>
    </tr>
    <tr>
      <td>IE00B1YZSC51</td>
      <td>iShares Core MSCI Europe UCITS ETF EUR (Dist)</td>
      <td>Dist</td>
      <td>696</td>
      <td>19,944</td>
      <td>475</td>
      <td>2.38</td>
    </tr>
    <tr>
      <td>IE00B4L5YX21</td>
      <td>iShares Core MSCI Japan IMI UCITS ETF USD (Acc)</td>
      <td>Acc</td>
      <td>522</td>
      <td>19,937</td>
      <td>-</td>
      <td>-</td>
    </tr>
    <!-- Total line -->
    <tr style='font-weight:bold; border-top:2px solid black; border-bottom:2px solid white'>
      <td></td>
      <td> Total </td>
      <td></td>
      <td></td>
      <td>99.633</td>
      <td>706</td>
      <td>0.71</td>
    </tr>
  </tbody>
</table>


### Value over time

Change in value of the portfolio over time, normalized to most current period. With the black line represting the closing prices of each trading day, and the red shadow indicating the daily spread between highest and lowest prices.

![Portfolio Value over Time](/assets/images/dashboard_portfolio_value_over_time.png){: style="text-align: center;"}

*Comments:* 
* The portfolio was bought some time ago, s.t. the portfolio holdings have the specified portfolio weights today. 


### Diversification

Regional diversification of the portfolio holdings at a specific date. The portfolio seems reasonably diversified when looking at regions. Within regions, there is a very high concentration on companies from the USA and Japan. 

<!-- <div class="row">
<div class="column">
<img src="/assets/images/dashboard_diversification_doughnut.png" alt="Diversification by Region" style="width:100%">
</div>
<div class="column">
<img src="/assets/images/dashboard_diversification_top10.png" alt="Diversification Top 10" style="width:100%">
</div>
</div>  -->

#### Diversification by Region
![Diversification by Region](/assets/images/dashboard_diversification_doughnut.png){: style="text-align: center;"}

\
#### Top 10 Holdings
![Diversification Top 10](/assets/images/dashboard_diversification_top10.png){: style="text-align: center;"}


*Comments:* 
* The country corresponds to the headquarter of the company. It does not mean that it is also the country where most of the revenue/profit is created. That is a topic for future analyses.
* The category "unknown" is a mapping problem. This requires a better data quality process for mapping iShares holdings to an ISIN.






