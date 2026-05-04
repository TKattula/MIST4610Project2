# MIST4610Project2

## Team Members
Tanvi Kattula [@Tkattula](https://github.com/TKattula) \
Maddie Wrigley [@Maddiekw1](https://github.com/Maddiekw1) \
Jessica Downen [@JessicaDownen](https://github.com/JessicaDownen) \
Darren Zhang [@darrenzhang11](https://github.com/darrenzhang11)

## Data Description
This dataset contains information regarding 115 indicators for chronic diseases that were developed by the CDC, CSTE NACDD. The dataset allows health professionals to understand trends nation-wide and state specific, and be able to understand health trends in their specific area. 

This dataset contains 34 columns, 10 of which are blank columns and are not used within the dataset at all and 309,216 rows. Each row contains information regarding the type of information collected, the topic, the location and many other thing. Below are the columns and thier datatype and a description of the columns use. 

### YearStart: 
Data Type: Numeric (Year)

Description: This column is important as it indicated the start year of when the data in the specific row began being collected.

### YearEnd: 
Data Type: Numeric (Year)

Description: This column is important as it indicated the last or final year the data in the specific row was collected.

### LocationAbbr: 
Data Type: String (Catagorical)

Description: This column is a abbrivation of the state that the data was collected in (i.e. GA).

### LocationDesc: 
Data Type: String (Catagorical)

Description: This column contains the same information as the column 'LocationAbbr', however this column display the states name is their full form (i.e. Georgia)

### DataSource: 
Data Type: String (Catagorical)

Description: This dataset pulls data from multiple sources like the BRFSS (Behavioral Risk Factor Surveillance System), US Cancer DVT and NVSS (National Vital Statistics System). This column allows us to identify where the specific rows gather their information from. This is vital as it allows us to understand what the data was being measured for and be able to identify the data within their respective sources.

### Topic: 
Data Type: String (Catagorical)

Description: This column is important as it allows us to understand the topic of the data in the row. The CDC included data on both the chronic illness itself and possible indicators in this field. For example, certain data was collected while gathering information on Cancer, so this row would have 'Cancer' as its input. Similarly, if data was collected on tobacco use as an indicator,  this row could also have 'Tobacco' as its input.

### Question: 
Data Type: String (Catagorical)

Description: This column is very important as it serves as the key resource in understand why the data was being collected. The question is essentially the reason for the collection the 'Why?'.

### DataValueUnit: 
Data Type: String (Catagorical)

Description: This column includes information regarding the data value. It is the unit of measurement. For example a percentage or per 100,000. 

### DataValueType: 
Data Type: String (Catagorical)

Description: This column includes information regarding the data value. It is the type of measurement used to collect the data. For example, the crude rate (total number of events) or age-adjusted rate.

### DataValue: 
Data Type: Numerical (float)

Description: This is the actual measurement of data. The value that was actually measured. 

### DataValueFootnotes: 
Data Type: String (Catagorical)

Description: This column includes information regarding the data value. This contain notes or relevent information regarding the data collection. Including "Data supressed; too few respondants or cases" or "No data available"

### LowConfidenceLimit: 
Data Type: Numerical (float)

Description: This column represents the lower confidence limit for the data in regards to its confidence interval. 

### HighConfidenceLimit: 
Data Type: Numerical (float)

Description: This column represents the higher confidence limit for the data in regards to its confidence interval. 

### StratificationCategory1: 
Data Type: String (Catagorical)

Description: This is the subgroup of people that were used to collect the data. Including age, gender, race, etc. 

### Stratification1: 
Data Type: String (Catagorical)

Description: This column refers to the specific subgroup used to collect the data. For example Sex = Female.

### Geolocation: 
Data Type: Mixed (Numerical and String)

Description: This includes the location of where the data was collect written in longitude and latitude. 

### Columns 19-22,27,30-34: 
Data Type: Mixed (Numerical and Catagorical)

Description: These columns are ID's for the location, topic, question, stratification and data value type columns.

## Questions and Their Importance
Question #1 \
In states with the highest chronic disease prevalence, are high-risk behavioral factors like tobacco use, alcohol consumption, and poor nutrition also elevated? Does this relationship suggest where prevention resources should be targeted?

**Why it is Important** --
This question is important because it helps identify whether chronic diseases are linked to preventable behaviors like smoking, alcohol use, and poor nutrition. If states with high disease rates also show high levels of these risk factors, it suggests that many of these health issues are not random but driven by lifestyle patterns. This has strong social and economic impacts, since chronic diseases increase healthcare costs, reduce productivity, and lower quality of life. It also matters for health, because understanding these relationships allows governments and organizations to focus on prevention instead of just treatment. Instead of spreading resources evenly, they can target the areas and behaviors that are actually causing the biggest problems. 

**How it ties into data set and further actions** -- 
This question ties directly into the dataset by comparing chronic disease prevalence with behavioral risk factors across states. This helps identify patterns or correlations between lifestyle behaviors and disease rates. Based on the results, actions could include targeting high-risk states with prevention programs like anti-smoking efforts or nutrition education, making interventions more focused and effective. 


Question #2 \
With West Virginia having the highest chronic disease burden, which chronic disease is most prevalent and which demographic groups are the most affected?

**Why it is Important** --
This question is important because it helps identify which chronic disease and group is the biggest issue specifically within the state of West Virginia. While question one focused on the behaviors to see how those could be prevented, this question is useful in determining where to send resources for those already affected. By specifically breaking down by disease type and then further by demographic such as age and race, it pinpoints a specific group that resources can be put towards to improve chronic disease numbers.

**How it ties into data set and further actions** -- 
This question ties into the dataset by looking at chronic disease prevalence across demographic groups within one geolocation in the dataset. This helps to take patterns from a high-level into a more zoomed-in focus to really allow a business to know exactly where resources are needed.

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
For question 2, to get the results we wanted, the question was better when broken down into 2 visualizations. For both visuals Location(State) field to was filtered to "WV" to ensure that data was only being shown for West Virginia.

On the first visual a couple more manipulations were made:\
First, the Stratification was filtered to include only age demographics, and second, the AGG(Chronic Disease Prevalence Score) was included in filters to ensure that only chronic diseases included in that score were included in this visual.

The columns were Topic (ie. chronic disease) and the rows were Stratification (ie. age demographic)  

On the second visual, different manipulations were made:\
First, the Topic field was filtered to "Cardiovascular disease" to show date for that chronic disease only. Next, the stratification field was set to be "Age >= 65" and all races, to get data for only those in the group we wanted to zoom in on. 

The columns were Stratification (ie. race demographic) and the rows were Topic (ie. chronic disease)

Both visuals have the labels and colors manipulated from AVG(DataValue).

## Analysis and Results
### Question #1

<img width="774" height="787" alt="image" src="https://github.com/user-attachments/assets/bd2cd9b0-cde3-455e-aa2b-2faac53bbe4f" /> \
The scatter plot comparing each state's Chronic Disease Score against its Risk Factor Score shows a clear positive correlation between behavioral risk factors and chronic disease burden across U.S. states. The upward sloping linear trend line confirms that states with higher behavioral risk factor prevalence (like tobacco or alcohol use) consistently tend to have higher chronic disease rates, suggesting the relationship is not coincidental but rather a meaningful pattern across the country.

The two average reference lines dividing the chart into four quadrants make it easy to identify which states are the most concerning. States appearing in the upper right quadrant are above the national average on both axes and have both elevated risk factors and elevated chronic disease rates simultaneously. These states, including Mississippi, West Virginia, Tennessee, and Arkansas, to name a few, are the clearest candidates for prevention resource prioritization. Their darker colored data points further reinforce that they carry the highest chronic disease burden in the dataset. On the opposite end, states like New Jersey, DC, and California fall in the lower left quadrant with below average scores on both measures, suggesting that their existing public health efforts may be producing better outcomes and could serve as models for higher burden states.

The overall implication of this analysis is that chronic disease burden and behavioral risk factors move together across states, meaning that simply increasing treatment in high burden states is unlikely to make a lasting improvement. Instead, the data supports directing prevention resources, like quitting tobacco programs, alcohol reduction initiatives, and nutrition and physical activity knowledge, would be most beneficial for the states identified in the upper right quadrant, where addressing the root behavioral causes has the most potential to reduce long-term chronic disease rates.


### Question #2

<img width="558" height="190" alt="Screenshot 2026-05-03 at 6 15 58 PM" src="https://github.com/user-attachments/assets/bf4067a4-ed00-462a-9cc9-79b7a82d980e" /><img width="700" height="135" alt="Screenshot 2026-05-04 at 1 53 38 PM" src="https://github.com/user-attachments/assets/f3cb292f-6ae8-45a4-87e0-791172a9457a" />

Starting with ther first visual, It is extremely evident that the most prevalent chronic disease is cardiovascular disease, especially in those over age 65. This age range especially for cardiovascular disease is not shocking as old age makes someone more prone to the disease. However, it is important to see that the average cases for this age demographic is way larger than other age groups or diseases. This shows that it is something to focus even more on for health professionals looking at disease treatment.

For the second visual, to further hone in on the affected demographics, it was best to look at race demographics only for the group age >=65 to draw relevant conclusions. From this we can see that the msot affected race is White non-Hispanic. This could be used to for professionals to look at genetic factors that may be impacted by race in disease treatments.

Overall, the visuals need one another to be viewed together to see the whole picture, but zooming in on West Virginia shows health professionals that the group in need of most resources are White non-Hispanics over the age of 65 that suffer form cardiovascular disease.

## Tableau Packaged Workbook
