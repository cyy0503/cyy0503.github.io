---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title: Analysis and insights from crime data on DUIs and car thefts in Los Angeles on Sundays
---

## 1.1 Page Introduction

At the end of March this year, a murder with a gun in Gotha sparked concerns about urban safety in Denmark, so in the case of San Francisco, which is also a big city, we wondered if we could get some insight from the statistical charts on the types of crime and the time of day, as well as the areas where the crime occurs more often than not.

In San Francisco, as in other large cities, crime fluctuates with the rhythm of the city. By analysing historical crime report data from the San Francisco Police Department, we can find some interesting patterns about how criminal activity changes over time. In particular, focusing on specific types of crime that occur on Sundays-vehicle burglaries and DUIs-reveals some unique aspects of city life.

Sunday, for many, is a time of rest and relaxation, a day to gather with family and friends. However, it is also a day that comes with an increase in specific criminal activities, particularly vehicle theft and DUI. Data shows that there is a significant increase in the incidence of these crime types on Sundays, which may reflect the fact that people are more likely to be out and about at the weekend, increasing the chances of vehicle theft. It also seems unsurprising that drink driving offences increase as people attend social events.

In this analysis, we will explore these patterns through three different types of data views: first, a time-series graph showing the distribution of crime events by hour of the day; second, a map view revealing the spatial distribution of crime across San Francisco's police districts; and finally, an interactive graph allowing users to customise their exploration based on the type of crime or timeframe. Together, these views paint a complex picture of criminal activity in San Francisco, providing insight into the city's security posture.

## 1.2 Dataset

Our dataset is provided by the City and County of San Francisco and owned by OpenData. It includes historical incident reports for the San Francisco Police Department from 2003 to March 2021, and we focus on 2003-2018, with a focus on 7 years of data analysis. The source dataset covers the public safety domain with tags including San Francisco Police Department, crime, police departments, and crime reports. Since its creation in February 2012, the dataset has been viewed over 225,000 times and downloaded over 70,000 times. The dataset is available under an Open Data Commons public domain dedication and licence. Because this journal primarily analyses data on DUI and car theft cases within it, the source link can be found on the San Francisco government's official website if you need to focus on other crime types.

# 2.1 24-Hour Comparison: Sunday Vehicle Theft vs. DUI Crimes

<img src="https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcR2uFt1th9-iwQytfSx2T_oAa_McNrrWBlX80h6h0yjXoEJJzW5" width="700" height="200"/>
    
                            Image source from ABC

![png](/pictures/output_5_0.png)

## 2.2 Editorial Critique

This polar graph clearly shows the 24-Hour Cycle of DRIVING UNDER THE INFLUENCE Crimes, it is clear that from from 21:00 p.m. until 2:00 a.m. is the peak time for the occurrence of DUIs, with a peak from 23:00 p.m. to close to 1:00 a.m., and the early morning hours from 4:00 a.m. to 13:00 p.m. is the lowest time of the day for the occurrence of crimes, this pattern of crime incidents is most likely due to the fact that the masses, mostly on Sunday evenings, carry out activities such as parties and other gatherings that require alcohol for relaxation, while relaxing their safety awareness of not being able to drink and drive. I think readers if family or friends in the party, drive to participate in the activities, perhaps can politely refuse to drink or in leaving the party, in advance to arrange a good chauffeur, for the sake of personal safety, I hope that we "drive not to drink, drink not to drive".

In contrast to the obvious pattern of drink driving, the pattern of vehicle theft during the 24 hours on Sunday does not seem to be immediately obvious, so let's analyse this time period in detail. After 17:00 p.m. and close to 19:00 p.m. is the highest occurrence of crime during the whole day on Sunday, while after 19:00 p.m. and between 23:00 p.m. is the second highest occurrence of vehicle burglary; between 16:00 p.m. and 17:00 p.m. and between 23:00 p.m. and 0:00 p.m., the number of burglary occurrences is very close to each other; for the daytime hours, between 4:00 a.m. and 8:00 a.m. is the least number of burglary occurrences in the whole day on Sunday. For daytime, 4 am to 8 am is the time of day on Sundays when the least number of burglaries occur. Based on the above analysis, I think readers may be able to reduce the likelihood of their vehicles being stolen by taking a little more time to lock their cars in the garage or checking that their vehicles are fully unlocked after dinner on Sunday nights.

 ## 3.1 Sundays: DUI and Vehicle Theft Areas Distribution

<embed src="/pictures/fig_vehicle_theft.html" width="400" height="300" type="text/html">
<embed src="/pictures/fig_dui.html" width="400" height="300" type="text/html">

## 3.2 Editorial Critique

Mission had the highest number of DUIs on Sunday with 186 cases, while the Tenderloin had the lowest with 35 cases. Interestingly, the Tenderloin also had the lowest number of vehicle thefts, indicating effective crime prevention measures such as stricter police patrols. Factors like nightlife activity and enforcement efforts influence DUI incidence. For more details, readers can refer to local law enforcement reports or contact LAPD directly.

The Tenderloin, with 1566 thefts, is the safest area on Sunday, while INGLESIDE, with 2846 thefts, is the worst. Factors like population density and parking availability influence burglary rates.

![jpg](/pictures/output_10_0.jpg)

                            Image source from ABC

PS: The above chart is the statistics shared by other websites about the top 10 most stolen vehicle brands in the U.S. Come and see if there's any of your car:)

## 3.3 Temporal Patterns of DUI and Vehicle Theft Crimes Throughout the Day (2010-2017)

<embed src="/pictures/plot.html" width="800" height="300" type="text/html">

# 4 Conclution

By mapping these crimes to different police districts in San Francisco, we can gain further insight into how certain areas are more likely to be hotspots for vehicle theft and DUI crimes on Sundays. This not only provides valuable safety information for residents and visitors, but also provides data to support law enforcement agencies in developing strategies to deploy resources more effectively, especially on weekends.

In addition, time-series analyses indicate that DUI offences are particularly concentrated during certain hours, which may be correlated with the closing times of bars and restaurants. This finding informs the development of targeted preventive measures, such as increasing patrols during key hours or working with local businesses to promote safe driving awareness.

Overall, through careful data analysis, we are able to not only reveal patterns of criminal activity, but also provide insights into reducing these crimes. By comparing crime data from San Francisco and Copenhagen, we may be able to identify similarities and commonalities in urban crime across different cultural and social contexts. Such cross-city and cross-cultural comparisons may provide valuable insights into global urban governance, prompting urban planners and law enforcement agencies to learn from the experiences of other cities and to work together to improve the safety and quality of life of urban residents.