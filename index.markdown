---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title: Analysis of street light conditions and urban safety in Washington DC
---

<embed src="/pictures/0_street_light_in_DC.html" width="800" height="800" type="text/html">

# 1.Motivation

Washington, D.C., is a quiet, uncluttered city. At sunset, take a walk in Washington Monument Square, dusk will surround the scenery rendered in a layer of hazy gold, lovers are holding hands, children are playing, vehicles are driving. As night falls, Washington's nightlife kicks off, and in the same time and space, the city's elegant and dignified daytime may be a quiet breeding ground for crime in some dark corners of the city at night...

If the streetlights in a city street malfunction, how does it affect the residents of the street at this very moment? Our attention was drawn to this by reading a predictive article about street lighting and crime rates: the author makes a bold prediction: 'Crime rates tend to fall when street lighting is damaged.' , a view that runs counter to our common sense: 'when streetlights are broken, crime rates predictably must rise', so we set out to analyse the current state of safety on Washington's city streets with this question in mind.

We have chosen three data sets to perform this analysis:
We have chosen three data sets to perform this analysis on.
Chinese:
1. the street light distribution dataset in Washington DC
2. 311_City_Service_Requests (street light downtime reports) in Washington DC
3. Washington DC's Neighbourhood Crash Data Set
4. crime dataset for Washington DC

The statistics on the strength of street lighting in Washington's neighbourhoods, as well as the city's safety conditions during the hours of street light failures, give us a grasp of the importance of city lighting for resident safety and traffic safety.
Good street lighting can significantly improve people's sense of safety at night. Adequately lit streetlights not only eliminate hidden dangers in the dark, but also effectively reduce crime rates, especially street crime such as theft and robbery. Residents feel safer as a result and are more likely to spend time outdoors at night.
In addition, improved street lighting enhances the safety of vehicles and pedestrians at night. Quality lighting conditions help to reduce the number of traffic accidents by giving both motorists and pedestrians a clear view of the road and potential hazards. This not only ensures the safety of pedestrians, but also improves the overall smoothness of traffic flow, creating a safer and more livable urban environment.


# 2. Data Analysis

## 2.1 Light and Shadows

### 2.1.1 Exploring Spatial Data and Crime Relationships

How does the size, geographic location, population density, and streetlight density of different boroughs affect crime rates in Washington, D.C.?

To do this, we first calculated the center coordinates of crime event locations for each Ward (`WARD`), which was determined by taking the average latitude (`Y`) and longitude (`X`) of the geographic location of the crime event. Then, the aggregated statistics of the number of crimes in each WARD, as well as the aggregated statistics of the number of street lights, were performed to visualize the situation of crime data and the number of street lights in each WARD.

From the graphs we can see that a high number of street lights does not necessarily lead to a direct reduction in crime. For example, even though WARD 2 has the highest number of streetlights (8,845), it also has the highest number of crimes recorded (27,787). This suggests that while increasing lighting can help illuminate, this measure alone is not effective in reducing crime, and that factors such as geographic location (whether it is in a central or peripheral area) need to be taken into account. Furthermore, WARD 3 has a relatively low number of crimes (8,570) despite having the highest number of street lights (10,465), which may be related to the socio-economic status and geographic location of the area.

<embed src="/pictures/1_bubble.html" width="800" height="800" type="text/html">

In our previous analysis, we collected `Area (sq mi)`, `Population Density (per sq mi)`, and `Streetlight Density` for each area and calculated a matrix of correlation coefficients between these data. Now, we will further analyze the correlation between these data and crime rates.

| WARD | Area (sq mi) | Population Density (per sq mi) | Streetlight Density | Crime Rate    |
|------|--------------|--------------------------------|---------------------|---------------|
| 0    | 2.2          | 38621                          | 2152.27             | 9895.45       |
| 1    | 7.9          | 8936                           | 1119.62             | 3517.34       |
| 2    | 9.1          | 6664                           | 1150.00             | 941.76        |
| 3    | 7.0          | 10888                          | 1560.14             | 1986.43       |
| 4    | 7.2          | 10124                          | 1449.86             | 3361.81       |
| 5    | 6.7          | 15545                          | 1237.01             | 2969.85       |
| 6    | 12.4         | 4646                           | 873.06              | 1611.21       |
| 7    | 16.6         | 3526                           | 453.07              | 933.25        |

|                             | Area (sq mi) | Population Density (per sq mi) | Streetlight Density | Crime Rate |
|-----------------------------|--------------|--------------------------------|---------------------|------------|
| **Area (sq mi)**            | 1.000000     | -0.797006                      | -0.952734           | -0.759634  |
| **Population Density (per sq mi)** | -0.797006 | 1.000000                      | 0.853791            | 0.961491   |
| **Streetlight Density**     | -0.952734    | 0.853791                       | 1.000000            | 0.813193   |
| **Crime Rate**              | -0.759634    | 0.961491                       | 0.813193            | 1.000000   |

The above analysis has identified several key correlations that are important for urban planning and public policy making.
- Larger areas tend to have lower population densities and street light densities, suggesting that a balanced allocation of resources needs to be emphasized in infrastructure planning for these areas.
- The strong positive correlation between population density and crime rates suggests that policymakers should increase security measures in densely populated areas.
- Although more street lights are usually aimed at reducing crime, the data show that areas with high street light densities also have higher crime rates, which may reflect a response strategy to high crime areas and points to the need for further research on the effectiveness of street light layouts in relation to crime prevention and control.

### 2.1.2 Immediate Impact of Street Light Outages

Street streetlights, although seemingly insignificant, play a key role in maintaining safety at night. To investigate the impact of streetlight damage on criminal activities, we use the GeoPandas library to transform the streetlight damage data, crime events, and streetlight data from city service requests into a geospatial format and standardize the coordinate system to UTM 19N. By setting up a 50-meter buffer zone around the streetlight damage point and performing spatial linking operations, we compare the crime records of the 24-hour period before and after the damage.

Surprisingly, the data analysis showed that the total number of crimes in the 24 hours after the damage was lower than before the damage. This finding challenges the conventional wisdom that the absence of streetlights directly increases crime rates. This may prompt us to reconsider the relationship between streetlights and nighttime crime.

<embed src="/pictures/2_total_crimes_before_after_24_hours.html" width="800" height="800" type="text/html">

A closer look at the graph below reveals that while there is an increasing trend in all thefts in the 24 hours following streetlight damage, there is a decrease in the number of other more serious crime types such as ROBBERY and BURGLARY. This finding is thought-provoking and suggests that streetlight failures may affect different types of criminal activity differently. The increase in thefts may be due to the lack of streetlights making it easier for thieves to remain hidden, while the decrease in serious crimes may be related to the fact that offenders are more likely to draw attention to themselves in darker environments.

<embed src="/pictures/3_proportion_crime_types_before_24_hours.html" width="800" height="600" type="text/html">

<embed src="/pictures/4_proportion_crime_types_after_24_hours.html" width="800" height="600" type="text/html">

### 2.1.3 Exploring Long-Term Crime Trends Following Street Light Failures

By previously collecting and analyzing crime data over a period of time before and after a failure, we have found that temporary failures of infrastructure are not going to lead to a significant increase in criminal activity, and that the number of crimes will even decrease within 24 hours of a failure such as a road failure. But does this effect diminish or persist over time?

To investigate this further, we calculated the median time from the start of street light damage (`ADDDATE`) to the time the repair was completed (`RESOLUTIONDATE`) and found that the average length of time a street light is repaired is about 12 days.

**Average resolution time: 11 days**

Based on the above information, we then counted the number of crimes in the two weeks before and after the point in time when the street light failure occurred, and found that the number of crimes fluctuated significantly in the 24 hours before and after the failure, and continued to show some smaller fluctuations in the following days. These circumstances reveal that the short-term effects of streetlight failures on criminal activity can be complex, while the long-term effects require further observation and analysis.

<embed src="/pictures/5_daily_crime_numbers_over_28_days.html" width="800" height="500" type="text/html">

So we continued to stretch the entire cycle and analyzed a trend graph of the number of crimes covering a total of 60 days before and after the streetlight failure and came to the following conclusions:

- Immediate Response to Failure: The trend graphs show a dramatic decrease in crime in the first 24 hours after a streetlight failure. This phenomenon may indicate that, despite the general belief that dark streets increase criminal activity, in the initial period, the lack of light may make offenders feel unsafe or unpredictable, thus inhibiting their criminal intent.
- Pre-Rehabilitation Dynamics (Days 1-12): In the 12 days or so prior to the streetlight rehabilitation, the number of crimes showed fluctuations with small amplitudes and long intervals between peaks. We gathered information that this may reflect both offenders and residents adapting to the changed lighting conditions. A relatively stable but slightly higher crime rate during this time may also indicate that the community is adjusting its behavioral patterns, such as by adopting alternative security measures or increasing informal surveillance.
- Post-rehabilitation fluctuations: After the streetlight rehabilitation, we noted an increase in the frequency of crime rate fluctuations, but the overall trend moved toward normalization comparable to pre-failure levels. This suggests that the rehabilitation of streetlights re-establishes a deterrent effect on potential criminal activity and emphasizes the importance of timely and effective maintenance of urban infrastructure.
<embed src="/pictures/6_daily_crime_numbers_over_60_days.html" width="800" height="500" type="text/html">

## 2.2 Analysing the correlation between street lighting and traffic accidents

### 2.2.1 The relationship between crash rates and street lights

By analysing some of the previous perspectives on the crime situation and degree of reins failure, we made some adjustments for the analysis of the relationship between traffic accidents and street lighting, first of all, perspective 1: the streets of Washington are divided into 8 administrative districts, so we first counted the total number of street lights in these administrative districts, and synchronously counted the number of car accidents in these districts, and observed whether there is a relationship

![本地图片](/pictures/7_comparison_crash_light_counts_by_ward.png)

This stacked bar graph shows the number of car crashes (in red) and the number of street lights (in blue) in each of the Washington Boroughs (Ward). This graph allows us to analyse the relationship between the frequency of crashes and the number of streetlights in different wards.

Ward 2 and Ward 3: These two wards have significantly more streetlights than the other wards. The low number of crashes in Ward 2 and the relatively moderate number of crashes in Ward 3 may indicate that the number of streetlights is not a single determinant of the impact of crashes. Ward 1, Ward 5, Ward 6, and Ward 8: These zones have low numbers of streetlights, with Ward 1 and Ward 6 having relatively high numbers of crashes. Ward 5 and Ward 8 do not have a significantly higher number of crashes than Ward 2 despite having a low number of street lights, suggesting that there may be other factors such as traffic flow and population density in the area that influence the occurrence of crashes. Ward 4 and Ward 7: The number of crashes in these two wards is relatively high, especially in Ward 7. Ward 7 has a relatively low number of streetlights, which may be a contributing factor to the higher number of crashes. Recommendations Increase the number of streetlights: In areas with a high number of crashes (e.g., Ward 4 and Ward 7), increasing the number of streetlights may help to improve the safety of nighttime driving. Integrate other factors: Analyse other factors such as traffic flow, level of development in the area, population density, etc., and assess their association with the occurrence of crashes in a comprehensive manner. Further detailed analyses: More detailed geospatial analyses of specific locations of crashes in each region to see the relationship between crash-prone locations and infrastructure such as street lights and traffic signs.

### 2.2.2 Analysis of car accidents in the 14 days before and after a street light failure

From the analysis above, we do find some relationship between streetlights and crashes, and next we analyse as a whole whether there is some link between the number of crashes when a streetlight failure occurs over the period 2019-2023. When analysing the crime dataset, we have already found that when a streetlight failure occurs in an area, there is not really a particularly significant trend in the number of crime incidents in that area in the 14 days before and after (in 3.1.2 it takes an average of 12 days for a streetlight to complete a report for repair), so we traversed the data on car crashes for 24 hours before and after the occurrence of a streetlight failure for each streetlight, that is, 48h before and after the point at which the streetlight failure occurs Might there be some surprising findings?

<embed src="/pictures/8_daily_crime_numbers_over_28_days.html" width="800" height="500" type="text/html">

Something amazing happened! Every street light near the car accident in before the failure is regular: we focus on the 14 days before the failure, the statistical graph is always like a sea wave from high to low and then gradually rise, but after the street light reported for repair, the overall trend in the street light failure until the repair of the overall trend in a straight line down, which and the crime of the same node of the time to analyse the same again! We venture to guess: after the street light failure, the street near the street should have taken in the failure out of the set up barricades or reminder signs of early warning, so as to remind passers-by and driving vehicles ahead of the road light failure, so the rate of car accidents dropped, and after the street light resumed normal use, our car accidents are back to the previous pattern of ups and downs like a wave.

## 2.3 Forecasting Future Traffic Accidents at Intersections

Based on the existing research, we can’t help but be interested in the relationship between car accidents and street lights in different directions at intersections every month in the future. I believe it can bring a new perspective to our research on street lights.We re-imported the data and further cleaned the data, deleted all rows that may have null values ​​in INTAPPROACHDIRECTION, and grouped them according to months and regions to get the number of occurrences in different months and regions.The aggregate data is stored in monthly_accidentsDataFrame.Use LabelEncoder() scikit-learn to encode the "INTAPPROACHDIRECTION" column into a numeric label. This is useful for algorithms that require numerical input.Because string values ​​are not accepted as input in machine learning.

We chose the random forest model as our machine learning model because of its advantages of high accuracy, robustness, and ease of interpretation.

Features and target variables:
X contains features ('month', 'INTAPPROACHDIRECTION') from Monthly_accidents DataFrame.
y contains the target variable ('Accident_Count') from the monthly_accidents DataFrame.

Training-test split:
Use the train_test_split function in scikit-learn to split the data into training and test sets. The test set size was specified as 20% of the total data, and a random state was set to ensure reproducibility.

<embed src="/pictures/9_car_accident_predictions_for_the_next_year.html" width="1000" height="500" type="text/html">

From this we can roughly see that in the next year there will be more car accidents in the three directions of the Middle East, North and South, and in the summer, there will be more car accidents in all directions. Therefore, we can increase the number of street lights in these areas. Coverage, especially at night and at dusk, improves driver visibility and reduces the occurrence of accidents. Secondly, through the intelligent management system, the brightness and opening time of street lights can be adjusted in real time based on historical accident data and prediction models. In this way, street lights can be managed in traffic-intensive areas and high-incidence periods according to actual needs, improving traffic safety.

# 3. Discussion

## 3.1 Analysis of predictive models

We built a machine learning model that predicts monthly car crashes based on INTAPPROACHDIRECTION. Month is treated as a categorical feature, making it possible to discover holiday seasons. Machine learning models can be scaled with multiple categorical features, such as weekdays; however, this can result in a model with too many features and is overly complex, possibly even overfitting. Summer vacation might also be a great addition.

Our hypothesis is that people are more likely to get into car accidents when passing through intersections due to the brightness of the lights and the clear road surface. However, because intersections tend to be in the four directions of east, south, west, and north rather than southeast, northeast, southwest, and northwest, the summed up numbers will be biased, but generally we can see that in a certain direction or in a certain season There are more accidents, this helps, we provide corresponding suggestions to the relevant departments

In addition, more feature values such as year, day, and weather can be introduced to predict specific feature vectors. In the future, the analyzed data can be used to make daily adjustments to street lights. Thereby minimizing the impact of car accidents caused by street lights on the basis of energy conservation and environmental protection.

## 3.2 Extended discussion of the combination of the three datasets of crime and car accidents as well as street lighting

There are actually many more factors that can be analysed for urban safety, in addition to the introductory and exploratory insights into the possible relationship between urban crime and traffic and street lighting that this project focused on. We found some clear patterns, particularly during streetlight failures, where the volume of traffic crashes and crime rates dropped dramatically at all locations, and as the streetlights returned to normal, they slowly rebounded to their previous frequency of occurrence.

The visualisations and accompanying explanations allow conclusions to be drawn quickly and intuitively, and provide some basic insights into the data used. However, the analysis is somewhat rudimentary and does not delve into deeper or more specific patterns, nor does it make use of specific statistical tools (e.g. machine learning) to identify behaviours. One interesting aspect that the analysis could be developed into is that it could be combined with some animated videos to illustrate the changes that occur between the three over time.

# Notebook link
[Explainer notebook](/pictures/project-assignment-b-notebook.ipynb)
