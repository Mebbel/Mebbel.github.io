---

title: "Extraction and transformation of ETF-Holdings"
# author: "Philipp Lang"
# is_post: true
permalink: /data_holdings/
# categories: Portfolio_Risk
# tags: [Investing, Data, PortfolioManagement]
toc: false
# toc_label: "Table of Contents"
# toc_icon: "cog"
# toc_sticky: true
classes: wide
---

Every ETF-provider provides information about holdings differently. To merge this data into one database, we need to uniquely identify securities. The keys will depend on the information provided and can differ across ETF-providers.

Aside from key-relevant data, ETF-providers deliver further information. Ideally, this information could be gathered to enrich the database. This section will determine if and which data meets minimum data quality criteria.


## Unique Identifiers (Keys)

To merge information from different data providers on security level, we need to be able to uniquely identify a security in each set with a key. The definition of the key will differ across and even within fund data providers.

Whereas Xtrackers and Lyxor provide a security ISIN for all of their products, iShares does so only for Debt ETFs. The unique identifier for securities in equity ETFs from iShares is a combination of (Symbol, Exchange).

The ETL requires a table a complete mapping of **(ISIN, Symbol, Exchange)**. This might need to be extended as the number of included data providers grows.

*(Note: Until 2021, iShares delivered an ISIN information on security level for Equity ETFs. Whereas the information pair of (Symbol, Exchange) still allows to uniquely identify a security, it is much more difficult to maintain. Every new security needs to be added and mapped to an ISIN manually.)*


## Available data and naming conventions

### Columns

Aside from key columns, ETF providers deliver other information as well. The extent and quality of information provided differs a lot. But, it might provide a good starting point for setting up larger mapping tables. The following sections will run primary checks on the data quality.


|----------+------+------+--------+----------+-----------------+---------+-----|
| Provider | ISIN | Name | Ticker | Exchange | SECTOR/INDUSTRY | COUNTRY | CCY |
| :--------|:-----|:-----|:-------|:---------|:----------------|:--------|:----|
| iShares  | ISIN | Name | Emittententicker  | Börse | Sektor  | Standort | Marktwährung |
| XTrackers| ISIN |	Name |	-	  | Exchange | Industry Classification | Country | Currency |
| Lyxor    | ISIN | SecurityName | - |	- 	 | -               | Country | LocalCurrencyCode |


### Security Names

The naming of securities seems to be somewhat standardized for equity securities. For debt securities, the conditions (e.g. principal, due date) are usually found in the naming as well. 

**Examples:**
* MICROSOFT CORP
* MICROSOFT CORPORATION
* MICROSOFT-T ORD
* MICROSOFT CORP 11/22
* MICROSOFT COR 2.525% JUN50 6/50

For the analysis, we do not need the name of the security for now, but rather the name of the issuing legal entity. For Microsoft, this would be "MICROSOFT CORPORATION" ([Source](https://search.gleif.org/#/record/INR2EJN1ERAN0W5ZP974){:target="_blank"}). Luckily, the GLEIF provides up to date mapping tables. ([Source](https://www.gleif.org/en/lei-data/gleif-concatenated-file/download-the-concatenated-file){:target="_blank"})


### Countries

The country column differs with each provider. This data cannot be used as is and would need extensive mapping tables.

**Examples:**
* GBR; Vereinigtes Königreich; Großbritannien (UK)
* USA; Vereinige Staaten; Vereinigte Staaten von Amerika

For our analysis, we will need information about the country on different levels: The location of headquarters and registration, but also the identification of geographic sources of revenue. Again, fortunately, the GLEIF provides the country of registration for each legal entity. The determination of geographic properties of revenue streams is a more complex topic.

In general, I will use the **ISO 3166-1 alpha-3** standard as a country identifier. A good alternative would be the numeric country codes from the IMF. One notable difference between the two systems is the status of Taiwan: Whereas there is an ISO3-Code for Taiwan, the IMF does not issue a numeric code.


### Sectors and Industries 

The assignment of sectors and industries to a company is somewhat ambiguous. For once, the determination of the industry is defined by the primary business activity of a company. Which can change over time and also be inconclusive.

For Microsoft, the provided sector and industry information is too messy and unfortunately unusable:

**Examples:**
* IT
* Information Technology
* Technologie
* Unternehmen
* Industrie
* Informationstechnologie
* Technology
* System-Software

Upon inspection of major data providers, for Microsoft, the sector appears to be assigned unanimously. Whereas the selected industry seems quite similar, the naming and details differ a bit. A more profound inspection is out of scope for now.


|---------------+------------+--------------------------|
| Source        | Sector     | Industry                 |
| :-------------|:-----------|:-------------------------|
| Bloomberg	    | Technology | Software & Tech Services |
| Reuters	    | - 	     | Software & Programming   |
| Yahoo Finance	| Technology | Software - Infrastructure|
| Nasdaq        | Technology | Computer Software: Prepackaged Software |

In preparation for possible future analyses, we need a standardized classification of sectors and industries. There are plenty of regional and international standards. To list a few:
* International: ISIC Rev. 4 
* European: NACE
* German: WZN 2008
* USA: SIC, NACIS

The obvious choice is **ISIC Rev. 4** ([Source](https://unstats.un.org/unsd/classifications/Econ/isic){:target="_blank"}) as the ETF portfolios to be analyzed can have exposure to any country in the world; in principle. Luckily, for many regional and national classifications, there are correspondence tables.

Yet, even with a classification system at hand, the actual assignment of sectors and industries is very complex and therefore out of scope for this section. There will be a section with more details in future.


## Summary

While the unique identification is possible with a few columns, some of them are time-consuming to maintain. Information provided along these key identifiers can only be used with highest awareness of the present data quality problems. The data is very messy and not standardized across ETF-providers.

For now, analyses can only executed on security and legal entity level. Any level of aggregation requires extensive mapping tables, which need to be created almost from scratch. That will take some time.
