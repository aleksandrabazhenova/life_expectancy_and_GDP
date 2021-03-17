# GDP and Life Expectancy

### INTRODUCTION

- This project explores the relationship between total GDP and the average life expectancy at birth for people in 6 countries - Chile (South America), China (Asia), Germany (Europe), Mexico (North America), USA (North America), and Zimbabwe (Africa).

- Several studies have been done over the decades to try to answer whether a relationship between GDP and life expectancy exists and many found some positive correlation. However, it’s crucial to recognise that the reality is far from simple.  While life expectancy may indeed increase with GDP at face value, there are other factors at play, such as how the money within the country is distributed among the people, how the money is spent (infrastructure, education, healthcare), and how the country makes it’s money in the first place (industrial activities, farming), all of which impact the average health and well-being of a nation.

- A 2000 paper[[1]] by an economics professor Christopher J. Ruhm, titled “Are Recessions Good for Your Health?”, showed that when the American economy is doing well, the mortality rate actually *increases*, thought to be the result of increased air pollution. Yet, data[[2]] from less developed nations, which increase their GDP mainly through farming activities, indicates that economic growth is associated with *better* overall health, implying that mortality is also affected by *how* a given country becomes wealthy in the first place.

[1]: https://academic.oup.com/qje/article-abstract/115/2/617/1840483
[2]: https://pubmed.ncbi.nlm.nih.gov/21074307/

### SCOPE

#### GOALS

- Understand what kind of relationship exists between life expectancy from birth and total GDP of a country.

#### ACTIONS

- If a relationship has been found:

    1. What further analysis can be performed to analyse the relationship?
    2. What other possible factors can affect life expectancy of a country?
    3. What other data can be collected an analysed to further support this finding?
    4. What other features can be considered in the analysis (gender, different causes of death)?

- If no relationship has been found or the results are inconclusive:

    1. What other features can be considered in the analysis (gender, different causes of death)?
    2. What other possible data can be looked at to find out the impact a country's GDP on its people's health?
    
#### DATA

- The data is stored in an CSV file and contains 4 columns: Country, Year, Life expectancy at birth (years), GDP.

- There are 6 countries - Chile (South America), China (Asia), Germany (Europe), Mexico (North America), USA (North America), and Zimbabwe (Africa).

- For each country, the average life expectancy at birth and total GDP is quoted for each year from 2000 to 2015 (16 entries for each country).

- There are no missing data for any country.

- There are 96 entries in total.

#### ANALYSIS

**The independent variable is GDP, and the dependent variable is life expectancy;**

- average life expectancy per country bar chart 
- average GDP per country bar chart
- trend of GDP per country over the years
- trend of life expectancy per country over the years
- correlation of life expectancy and GDP per country (scatter graphs on single plot + individual)

### EVALUATION OF RESULTS

#### AVERAGE LIFE EXPECTANCY OVER 15 YEARS

- Initially, the average life expectancy at birth for each country was calculated. From Figure 1.1 shows that, apart from Zimbabwe (Africa), the average life expectancy for the other 5 countries is fairly close, all within the range of 74-80 years. Germany has the highest life expectancy at birth  of 79.66 years, while Zimbabwe’s has the lowest average life expectancy of 50.09 years. China has the second lowest life expectancy of 74.26 years.

- Further analysis was done to determine whether any statistically significant difference exists between Chile, China, Germany, Mexico, and USA (not counting Zimbabwe, since its life expectancy is so radically different).

- For an Anova test, the following null and alternative hypothesis were formulated:
	1. Null: there is no statistically significant difference between the average life expectancies of Chile, China, Germany, Mexico, and USA.
	2. Alternative: there is a statistically significant difference between the life expectancies of the above 5 countries, and their samples come from different populations with different life expectancy averages.

- A significance threshold of p = 0.05 was set.

- The following assumptions were made:
	1. the average life expectancy per year for a given country was obtained by randomly sampling from the country’s population
	2. average life expectancy per year of a given country is independent from another country
	3. life expectancy over the 15 year period is approximately normally distributed for each country
	4. the standard deviations of those distributions are approximately equal

- It is fair to assume that assumptions 1 and 2 are valid. To validate assumptions 3 and 4, a KDE plot was generated and the standard deviations calculated. From Figure 1.2, it can be seen that none of the distributions are normal, exhibiting a varying degree of skew and modality. China’s and Mexico’s distributions are the closes to normal, while USA, Chile and Germany appear to be bimodal. It is not immediately clear what feature could be the cause of this bi-modality.
- The standard deviations also did not validate the assumption, with China’s standard deviation being more than twice that of Mexico.
- If these facts were to be ignored, and the Anova test were to be carried out anyway, it would become apparent that there exists at least one pair of countries, for which there exists a statistically significant difference in average life expectancies, with a p value of 5.993e^-27.
- Tukey’s range test confirmed that for all pairs, apart from Chile-Germany and Chile-USA, one can reject the null hypothesis. for Chile-Germany and Chile-USA the test was not able to confirm that any statistically significant difference exists between the averages of their life expectancies.
- However, since assumptions 3 and 4 are violated, it is not clear how meaningful the result of this test is.

#### AVERAGE TOTAL GDP OVER 15 YEARS

- A 15 year average value of each country’s GDP was plotted and calculated. Unlike for life expectancy, these results are all strikingly different. USA has the highest total GDP average of 14,075.00 billion USD, while Zimbabwe has the lowest average GDP of 9.06 billion USD. Chile has the second lowest average GDP of 169.79 billion USD.
- At this stage, it is clear that the relationship between high GDP and high life expectancy is not clear cut. The wealthiest country (USA) doesn’t have the highest life expectancy, even those its average GDP towers above the rest of the countries, including Germany.

#### GDP AND LIFE EXPECTANCY TRENDS

- While averages are good at giving a rough idea of which country has the best or worst GDP and life expectancy, they are not helpful for finding trends. It’s important to consider how these features change and fluctuate together over the 15 year period.
- In order to plot GDP and life expectancy trend on the same axis, the data was firstly normalised using the min-max normalisation method individually for each country.
- Figure 3.1 shows the trend of normalised GDP and life expectancy, revealing that fro each country a positive trend exists for both features, which, at first glance, seem to be closely related.
- For Chile, Germany, Mexico, USA, and Zimbabwe, GDP and life expectancy seem to go hand-in-hand. However, upon closer inspection, when some countries experience a peak or fall in GDP, this is not always accompanied by an immediate peak or drop in life expectancy.
- China’s GDP and life expectancy trend also follows a similar positive trend, however, the graph looks unusually smooth, which begs the question of whether was is a significant difference in how the data was collected and if this could have introduced inaccuracies into the data.

#### GDP AND LIFE EXPECTANCY CORRELATION

- To truly understand whether GDP affects life expectancy, if at all, one must consider the strength of the correlation between these features. For this, linear regression plots were generated and the correlation coefficients were calculated between GDP and life expectancy.
- Figures 4.2 through 4.7 show the individual linear regression plots for each country. Chile, Germany, Mexico, USA, and Zimbabwe all show a strong positive correlation. China, too, shows this, however, the relationship may not be linear.
- the Pearson correlation coefficients are as follows: 

	- Chile: 0.9498766659254415
	- Chine: 0.9085255408648358
	- Germany: 0.9326988982561268
	- Mexico: 0.9322377167847082
	- USA: 0.9817092382430257
	- Zimbabwe: 0.9661998955858779]

### CONCLUSIONS

- There is a strong positive correlation between total GDP and life expectancy at birth for each of the 6 countries considered, assuming a linear relationship between the two features.
- A clear positive trend in both, total GDP and average life expectancy at birth was observed for each country. Broadly speaking, the two trends appear to go hand in hand over the 15 year time scale. Over short time scales, this is not always the case, since during some years when GDP changed sharply, life expectancy at birth was either not affected or saw a change in the opposite direction to the GDP.
- Looking at the average total GDP and average life expectancies at birth over the 15 years, it is apparent that the highest GDP does not correspond to the highest life expectancy at birth.
- Overall, while a positive correlation is present, it is clear that GDP is not the direct factor that impacts average life expectancy at birth within a nation. It is possible that GDP affects some other factors, which in turn have a more direct impact on the life expectancy within a nation. For example, GDP might affect access to education and healthcare differently in different countries, or GDP may correlate with medical infrastructure and access to the latest medical innovations within a country, all of which play a vital role in determining whether someone lives or dies.

### FURTHER ACTIONS

- To dig deeper into the correlation between GDP and life expectancies, the following needs to be considered:

	1. GDP per capita instead of total GDP
	2. Leading causes of death for each country to identify outliers
	3. More countries to represent each continent
	4. More samples (longer time frame) for each country to identify potentially bigger trends
	5. Different ways life expectancy can be quantified and the biases each one potentially introduces
	6. How each country creates its economic wealth split into categories (industrial, technological, agricultural etc)
	7. Which countries are affected by war, environmental disasters, or national health crises
	8. How the wealth in each country is distributed
	9. The percentage of people in the country that have access to education, healthcare, clean water
	
