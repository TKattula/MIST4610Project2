# MIST4610Project2

## Team Members
Tanvi Kattula [@Tkattula](https://github.com/TKattula) \
Maddie Wrigley [@Maddiekw1](https://github.com/Maddiekw1) \
Jessica Downen [@JessicaDownen](https://github.com/JessicaDownen) \
Darren Zhang [@darrenzhang11](https://github.com/darrenzhang11)

## Data Description

#### YearStart: 
Data Type: Numeric

Description: This column is important as it indicated the start year of when the data in the specific row began being collected.

#### YearEnd: 
Data Type: Numeric

Description: This column is important as it indicated the last or final year the data in the specific row was collected.

Together, the start year and end year is the period of time (in years) where the data specific to the row was collected.

#### LocationAbbr: 
Data Type: String (Catagorical)

Description: This column is a abbrivation of the state that the data was collected in (i.e. GA).

#### LocationDesc: 
Data Type: String (Catagorical)

Description: This column contains the same information as the column 'LocationAbbr', however this column display the states name is their full form (i.e. Georgia)

#### DataSource: 
Data Type: String (Catagorical)

Description: This dataset pulls data from multiple sources like the BRFSS (Behavioral Risk Factor Surveillance System), US Cancer DVT and NVSS (National Vital Statistics System). This column allows us to identify where the specific rows gather their information from. This is vital as it allows us to understand what the data was being measured for and be able to identify the data within their respective sources.

#### Topic: 
Data Type: String (Catagorical)

Description: This column is important as it allows us to understand the topic of the data in the row. The CDC included data on both the chronic illness itself and possible indicators in this field. For example, certain data was collected while gathering information on Cancer, so this row would have 'Cancer' as its input. Similarly, if data was collected on tobacco use as an indicator,  this row could also have 'Tobacco' as its input.

#### Question: 
Data Type: String (Catagorical)

Description: This column is very important as it serves as the key resource in understand why the data was being collected. The question is essentially the reason for the collection the 'Why?'.

#### Question: 
Data Type: String (Catagorical)

Description: This column is very important as it serves as the key resource in understand why the data was being collected. The question is essentially the reason for the collection the 'Why?'.




## Questions and Their Importance
Question #1 \
In states with the highest chronic disease prevalence, are high-risk behavioral factors like tobacco use, alcohol consumption, and poor nutrition also elevated? Does this relationship suggest where prevention resources should be targeted?

Why it is Important 
This question is important because it helps identify whether chronic diseases are linked to preventable behaviors like smoking, alcohol use, and poor nutrition. If states with high disease rates also show high levels of these risk factors, it suggests that many of these health issues are not random but driven by lifestyle patterns. This has strong social and economic impacts, since chronic diseases increase healthcare costs, reduce productivity, and lower quality of life. It also matters for health, because understanding these relationships allows governments and organizations to focus on prevention instead of just treatment. Instead of spreading resources evenly, they can target the areas and behaviors that are actually causing the biggest problems. 

How it ties into data set and further actions 
This question ties directly into the dataset by comparing chronic disease prevalence with behavioral risk factors across states. This helps identify patterns or correlations between lifestyle behaviors and disease rates. Based on the results, actions could include targeting high-risk states with prevention programs like anti-smoking efforts or nutrition education, making interventions more focused and effective. 


Question #2

## Manipulations

### Question 1 Manipulations:

To prepare the data for analysis, several filters and calculated fields were applied in Tableau.

First, the StratificationCategory1 field was filtered to "Overall" across all visualizations to ensure we were analyzing the general population rather than specific demographic subgroups like age, sex, or race/ethnicity. This kept the comparisons between states consistent.

Second, the DataValueType field was filtered to "Age-adjusted Prevalence" for the chronic disease visualizations. Age-adjusted prevalence accounts for differences in age distribution between states, making it a fair and accurate way to compare disease burden across states with very different populations. Without this adjustment, states with older populations would appear to have higher disease rates simply due to demographics rather than true disease burden.

Two calculated fields were also created to help analyze the question:

Chronic Disease Score — This field calculates the average age-adjusted prevalence rate across five major chronic disease topics: Cardiovascular Disease, Diabetes, Asthma, Arthritis, and Mental Health. The formula used was:\
AVG(IF [Topic] = "Cardiovascular Disease" OR [Topic] = "Diabetes" OR [Topic] = "Asthma" OR [Topic] = "Arthritis" OR [Topic] = "Mental Health" THEN [DataValue] END)

This gave each state a single composite score that represents its overall chronic disease burden.

Risk Factor Score — This field calculates the average prevalence rate across three behavioral risk factor topics: Tobacco, Alcohol, and Nutrition, Physical Activity, and Weight Status. The formula used was: \
AVG(IF [Topic] = "Tobacco" OR [Topic] = "Alcohol" OR [Topic] = "Nutrition, Physical Activity, and Weight Status" THEN [DataValue] END)

This gives each state a single composite score that represents its overall behavioral risk factor burden.

These two scores were then plotted against each other in a scatter plot to examine the relationship between risk factors and chronic disease rates across states. A linear trend line was applied to clearly show the correlation between the two scores across states. Two average reference lines were also added to divide the scatter plot into four quadrants to make it easy to identify which states fall above or below the national average on both measures. Data points were color coded by Chronic Disease Score so that the highest burden states appear as the darkest dots, adding a third dimension to the visualization and making priority states immediately clears.


### Question 2 Manipulations:

## Analysis and Results
### Question #1

<img width="774" height="787" alt="image" src="https://github.com/user-attachments/assets/bd2cd9b0-cde3-455e-aa2b-2faac53bbe4f" /> \
The scatter plot comparing each state's Chronic Disease Score against its Risk Factor Score shows a clear positive correlation between behavioral risk factors and chronic disease burden across U.S. states. The upward sloping linear trend line confirms that states with higher behavioral risk factor prevalence (like tobacco or alcohol use) consistently tend to have higher chronic disease rates, suggesting the relationship is not coincidental but rather a meaningful pattern across the country.

The two average reference lines dividing the chart into four quadrants make it easy to identify which states are the most concerning. States appearing in the upper right quadrant are above the national average on both axes and have both elevated risk factors and elevated chronic disease rates simultaneously. These states, including Mississippi, West Virginia, Tennessee, and Arkansas, to name a few, are the clearest candidates for prevention resource prioritization. Their darker colored data points further reinforce that they carry the highest chronic disease burden in the dataset. On the opposite end, states like New Jersey, DC, and California fall in the lower left quadrant with below average scores on both measures, suggesting that their existing public health efforts may be producing better outcomes and could serve as models for higher burden states.

The overall implication of this analysis is that chronic disease burden and behavioral risk factors move together across states, meaning that simply increasing treatment in high burden states is unlikely to make a lasting improvement. Instead, the data supports directing prevention resources, like quitting tobacco programs, alcohol reduction initiatives, and nutrition and physical activity knowledge, would be most beneficial for the states identified in the upper right quadrant, where addressing the root behavioral causes has the most potential to reduce long-term chronic disease rates.


### Question #2

## Tableau Packaged Workbook
