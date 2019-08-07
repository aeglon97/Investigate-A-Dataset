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

### Results:

**Overall**
1. Earthquakes killed more people on average for all years at a mean of 218 people. Contrarily, floods killed the least amount of people, at 35 people on average.
2. For all countries and years, around 7 people are killed per 100,000. At maximum, 131 people are killed per 100,000.
3. Of all the natural disasters, droughts have the highest standard deviation at 5158 people - meaning droughts have the highest variability in mortality counts compared to all natural disasters.
4. The average total forest area for any given country/year pair is 18,615 square kilometers.
5. There is higher variability in female BMI scores in comparison to male BMI scores. However, the mean female BMI score is greater than the mean male BMI score.
6. Floods happen the most but kill the least, while earthquakes happen the least but kill the most.

**Question 1:** Murder Rate by Country and Year
1. Guatemala in the year 1981 had the highest global murder rate at 131 per 100,000 people.
2. Guatemala in 1981 is, in fact, a global outlier for murder rates. These were the years during which the Guatemalan Civil War took place.

**Question 2**: Total Forest Area and Death by Drought
1. The more total forest land a country has, the less likely the average citizen will die by drought.
2. I received a coefficient of 0.0000038 and a p-value of 0.174 after implementing a linear regression model.
3. With a Type I Error threshold at 0.05, the p-value indicates that total forest area is not statistically significant in predicting the counts of death by drought.

**Question 3**: Total Forest Area by BMI Scores and Gender
1. The less forest area a country has in any given year, the more variability there is in the range of BMI scores for both genders.
2. There are only 3 countries with no forest area: Qatar, Nauru, and San Marino. 
3. 34 countries have shown a constant decrease in forest area by year, whereas only 12 countries have shown a constant increase in forest area by year. This means that more countries are losing forest land than gaining.
4. The top 10 countries with the most forest area is either a world superpower, contains a rainforest climate, or both.
5. The bottom 10 countries with the least forest area is at least 1 of the following: a majority/arid climate, a heavily industrialized country, and/or currently experiencing warfare and crisis.
6. There is a good amount of variability of whether men or women are more overweight in any given total forest area. Therefore, this relationship is inconclusive.

**Question 4**: Natural Disaster Death Counts by Murder Rates
1. For all natural disasters except floods, the higher the natural disaster mortality count, the lesser the murder rate. 
2. To combat the provided limitation below, I implemented 5 linear regression tests between murder rate and all 5 natural disaster death counts.
3. With a Type I error threshold at 0.05, the only statistically significant relationships were Murder Rate vs.***Epidemic Killed*** and Murder Rate vs. ***Storm Killed***, with p-values of 0.00004 and 0.00256 respectively.
4. The r-values for ***all my models*** are between 0.0 and 0.30, declaring that all relationships are weakly correlated.

### Limitations:

**Overall**
1. Not only did our `df_tsunami` dataset contain the least amount of records, it was filled with NaN values. I had to drop this dataset entirely, bringing down our natural disaster variables from 6 to 5.
2. There were 26 NaN values in the `df_forest_area` dataset. Luckily, these all belonged to only 1 country - South Sudan - and so we only had to drop 1 row from the entire dataset.
3. For `df_murder`, out of 206 countries, 198 had missing records. I had either 2 choices: fill in all the NaN data, or drop this dataset entirely. Since murder rates was one of my main variables of interest, I decided instead to keep the NaN values.
4. `df_epidemic` was missing the year 1973. Therefore, when correlating other variables with counts of death by epidemic, I had to accept that this single year would be missing from our analysis.

**Question 1**
1. The trend for murder rates by year for Guatemala have largely been unpredictable and varied between the mid 1970s to late 1980s.

**Question 2**
1. Outliers heavily affect the distribution of forest land vs. death by drought. Taking away all outliers would render an unclear distribution, though it would be slightly right-skewed.

**Question 3**
1. Countries with 0 square kilometers of total forest area have the most variability among BMI rates, which means making visual assessments based on this large number of outliers was difficult to do.

**Question 4**
1. The majority of the data for death counts by natural disaster clustered around 0. Excluding this cluster of data would be impractical because that'd mean excluding the majority of the data. On the other hand, focusing solely on the outliers would mean ignoring the majority of data again. 