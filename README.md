# unhcr

This repository contains a commented Jupyter Notebook as part of a project attempting to forecast asylum applications using data from a number of sources:

[UNHCR Asylum Applications](http://popstats.unhcr.org/en/asylum_seekers_monthly)

[World Bank Inflation Indices](https://data.worldbank.org/indicator/fp.cpi.totl)

[ACLED conflict event data](http://acleddata.com/)

[UN population data](https://population.un.org/wpp/)

[WFP food prices](http://foodprices.vam.wfp.org/Analysis-Monthly-Price-DataADV.aspx)

[World Bank GDP per capita data](https://data.worldbank.org/indicator/ny.gdp.pcap.cd)

The task was to use some of this background information in order to predict asylum applications over a three-year period. That is, using conflict etc. data from, say, 2015 in, say Angola, to predict asylum applications from Angolans over the years 2016-2018.

We didn't end up using all of these variables. In the end, we fit a Random Forest Regression model using sklearn. In the exploration process, I started off fitting models using only population and conflict data, just to get a feel for things. These did...okay, with R-squareds in the .50ish range. That's to be expected without a baseline. Once I added in the number of asylum applications received in the *current* year, the model started to perform consistently in the 0.88-0.92 range.

That's deceptive-- the model performs extremely well for some asylum-seeker # ranges and extremely well for some countries; it nearly always gets the order of magnitude right in its predictions, but is sometimes off by 50% or more. It performs considerably better at prediction than our attempts with generalized linear models, but the inconsistency of prediction accuracy--or perhaps precision--is an area of improvement. We can probably squeeze some more efficiency out of this model by 1) doing a better job cleaning and merging the data and 2) accounting for region-level variables such as climate and distance from Europe. Asylum seekers generally must apply *in* the country in which they're seeking asylum, so even if a country is producing large numbers of refugees, it will typically only produce large numbers of *asylum-seekers* if those seekers can easily get to e.g. Europe.
