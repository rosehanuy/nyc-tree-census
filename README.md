# CO2 Sequestration in NYC Street Trees from 1995 - 2015

This project uses NYC tree census data from 1995 and 2015 to estimate how much CO2 was stored in that 20-year period by the city's largest tree species.

## Methods

* Identify which species included most of the largest trees (defined as above average diameter-at-breast-height (dbh)) for each year.
* Determine CO2 stored by these species in 1995 and 2015 using process outlined by the US Forest Service. 
* Visualize results with bar and pie charts.

## Data

* NYC Tree Census data from [1995](https://data.cityofnewyork.us/Environment/1995-Street-Tree-Census/kyad-zm4j) and [2015](https://data.cityofnewyork.us/Environment/2015-Street-Tree-Census-Tree-Data/uvpi-gqnh)
* Allometric equations for estimating tree dry weight biomass from [USDA Urban Tree Database](https://www.fs.usda.gov/rds/archive/Catalog/RDS-2016-0005)

## Results

After removing outliers from the data, I compared diameter-at-breast-height (dbh) values from each year. The 1995 mean dbh was 9.93 inches and the 2015 mean dbh was 11.09 inches. The city's 'large' trees were defined as those with a dbh larger than the mean. 

![boxplot](/images/boxplot.png)

I then identified the species that had most of the city's largest trees. The rest of the analysis focuses on these species. 

- In both years, most of the larger trees in the city were London Planetrees. 
- Sycamore Maple, Ginkgo, and Sugar Maple appear only in 1995.
- They are replaced by Japanese Zelkova, Green Ash and Callery Pear in 2015.

![barchart](/images/species_counts_resize.png)

The next step was to calculate the CO2 stored by these species each year.

According to the USDA [Urban Tree Database](https://www.fs.usda.gov/psw/publications/documents/psw_gtr253/psw_gtr_253.pdf), the process for calculating the amount of CO2 sequestered in a tree is as follows:
- Find the aboveground dry weight biomass of the tree by using the species-appropriate allometric equation.
- Multiply the this biomass by 1.28 to incorporate belowground biomass.
- Multiply by the constant 0.5 to convert to total carbon stored in kg.
- Multiply by the constant 3.67 (the molecular weight of CO2) to convert to the total CO2 stored in kg.

My [code](https://github.com/rosehanuy/nyc-tree-census/blob/main/carbon_storage.ipynb) for completing this process produced the following results.

![barchart2](/images/co2_barchart.png)

![piechart](/images/co2_piecharts.png)

* The three species that showed the greatest increase in CO2 storage over the 20 year period were Pin Oak, London Plane, and Honeylocust. 
* In both years, Londonplane trees stored the most CO2. This species stored 1.02x10^8 kg of CO2 in 1995 and 2.57x10^8 kg in 2015. 
* Interestingly, all threes species of Maple - Red Maple, Silver Maple, and Norway Maple - diminished in terms of their relative share of CO2 sequestered in 2015 compared to 1995. The bar chart above shows that these three species also all diminished in terms of absolute number of individuals.
