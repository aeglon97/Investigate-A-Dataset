# Investigate-A-Dataset: ***Finding Correlations Among Seemingly Unrelated Variables***
 
 
## Motivation

For this project I gathered data from 4 different datasets off of Gapminder, assessed and cleaned the data, and stored it all in a final, clean CSV. Afterwards, I posed my own research questions, explored the data, and reported my findings.

## Introduction

**Broad question:** How do total forest area and frequency of natural disasters shape a country's obesity rates and murder rates?

> I picked these factors which seem to be unrelated: frequency of natural disasters, to rates of obesity and murder, to formulate new interesting questions and uncover unexpected patterns. I also wanted to approach this project through an experimental and free-for-all lens, just to see if I can make any fun or comical conclusions from the giving unrelated datasets. I received all of my data through GapMinder.

Here is a breakdown of my final clean CSV's features, `gapminder_all.csv`:

- **country**
- **year**

***Natural Disasters***
- **drought_killed** 
- **earthquake_killed**
- **epidemic_killed**
- **flood_killed**
- **storm_killed**

***Total forest area in square kilometers***
- **total_forest_area**

***Average bmi rate by country and year***
- **female_bmi**
- **male_bmi**

***Counts of death by murder per 100,000***
- **murder rate** 

## Research Questions

**Question 1:** Which country has the highest homicide rate? What about just country? Or year? Is this an outlier?

**Question 2:** Do countries with less forest area tend to have higher rates of death by drought?

**Question 3:** How much have global obesity rates changed in countries with high forest area vs. countries with low forest area?

**Question 4:** Does a country’s likelihood of experiencing a natural disaster correlate with the homicidal tendencies of its citizens?

## Findings

**This project was done under the intention of finding relationships among seemingly unrelated variables. For the relationships in questions 3 and 4, I have not found any substantial, eye-opening relationships.**

For **Question 1** I discovered that Guatemala had the highest murder rate at 131 people per 100,000 and this took place in the year 1981, which housed the global highest recorded homicide rate. To explore further, I asked the question, **How do murder rates for Guatemala vary by year?** I discovered that ***Guatemala in 1981, in fact, is a global outlier for murder rates.*** Furthermore, the trend for murder rates by year for Guatemala have largely been unpredictable and varied between the mid 1970s to late 1980s. These years also depicted the record highest and lowest murder rates for Guatemala, adding further to that picture of instability. After doing further research, I learned that ***this is the same exact year range that the Guatemalan Civil War took place.***


For **Question 2**, I discovered that the ***more the forest land, the less likely the average citizen is to die by drought.*** This conclusion was reached after generating a scatterplot. However, the downside is that all points are clustered around the point (0, 0), and most points never go beyond y = 250. If we took away all outliers, the skew/distribution would be largely unclear though slightly right-skewed. To combat this, I implemented a linear regression test between the 2 variables with death by drought as the dependent variable. My Ordinary Least Squares regression model gave a coefficient of 0.0000038, which implies a ***weak positive linear relationship.*** However, the ***p-value was calculated to be 0.174, and when compared to a Type I error threshold of 0.05, this implies that total forest area is not statistically significant in predicting the counts of death by drought.*** This defeats my initial intuition that the more forest a country has, the more likely it is to have rivers and other sources of water, thus having lesser rates of death by drought.

For questions 3 and 4, I look at relationships between seemingly unrelated variables.**

For **Question 3**, I examined the relationship between BMI scores and total forest area in square kilometers. I discovered that the less forest area a country has in any given year, ***the more variability there is in the range of BMI scores for both genders.*** In the total forest area range between 0.5km^2 and 0.8km^2, BMI scores depict a negative linear trend for both genders. Overall, countries with 0.0 square kilometers of total forest area have the most variability among BMI rates, and there is a good variability of whether men or women are overweight based on total forest area.

To explore the question further, I discovered that ***there are only 3 countries with no forest land: Nauru, Qatar, and San Marino.*** 34 countries have shown a constant decrease in forest area by year, where there are only 12 countries depicting a constant increase in forest area by year. Thus, ***more countries are losing forest land than countries that are gaining.*** Additionally, the top 10 countries with the most forest area have either is a world superpower, contains a rainforest climate, or both. On the flipside, the bottom 10 countries with the least amount of forest area is at least 1 of the following: a majority desert/arid climate, a heavily industrialized country, and/or currently experiencing warfare and crisis.

For **Question 4**, I examined the relationship between death by natural disaster and murder rates. Did the likelihood of experiencing a natural disaster correlate with the homicidal tendencies of the citizens? The plots generated implied that ***for all natural disasters except floods, the more natural disaster mortalities there are, the lesser the murder rate.*** However, I discovered that the majority of the data for death counts by natural disaster clustered around 0. We could not just exclude these "clusters" in our analysis because they contain the majority of data. On the other hand, focusing on the outliers solely would mean ignoring the majority of data.

To combat this problem, I decided the best approach was to individually generate another linear regression test for murder rates vs. all 5 natural disaster death counts. After establishing a Type I error threshold at 0.05, the only statistically significant relationships were ***Murder Rate vs. Epidemic Killed*** and ***Murder Rate vs. Storm Killed***, with p-values of 0.00004 and 0.00256 respectively. The ***r-values for all my models are between 0.0 and 0.30***, declaring that all the relationships are weakly correlated. 
