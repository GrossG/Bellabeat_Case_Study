# Bellabeat_Case_Study

## Background
Bellabeat, a hightech manufacturer of smart health-focused products for women, was founded in 2013 by Urška Sršen and Sando Mur. This technology design was designed by Sršen's background as an artist. 

Bellabeat had devolved a worldwide presence by 2016, and although focusing on digital marketing, has also invested in many traditional avenues of advertisting; radio, billboards, print, and television.

To get to the next level, Sršen knows the importance of utilising available consumer data; asking the marketing analytics team to analyse data of their products. High-level recommendations are hoped to come from this, which can shape Bellabeat's marketing strategy. 


## Ask
To analyse smart device usage data on non-Bellbeat smart devices, from which insights can be used on one Bellabeat product. 

### Stakeholders
* **Urška Sršen**: Cofounder and Chief Creative Officer
* **Sando Mur**: Cofounder and key member of the Executive Team
* **Marketing Analytics Team**: Responsible for collecting, analysing and reporting data, to help outline Bellabeat's marketing strategy.  


## Prepare
### Dataset information
* This data set was taken from FitBit Tracker Data [available on Kaggle](https://www.kaggle.com/datasets/arashnic/fitbit). 
* It is split into 18 Excel spreadsheets, based on different information such as daily activity, calories burnt per hour and steps taken per day. 
* This data was collected via survey between 3 December 2016 and 5 December 2016 and undertaken by Amazon Mechanical Turk. 

### Is the data ROCC?
#### Reliability 
*   Low; the file with the highest number of respondents had 33

#### Original
*   No; the data was recorded by Amazon Mechanical Turk

#### Comprehensive
*   Medium; there is insightful information, but spread among a number of files

#### Current
*   No; the data is over 6 years old

#### Cited
*   No; the data is taken from a third party

## Process
### Upload
* I downloaded the above data from Kaggle onto my computer; the 18 CSV files.
* Some files were far too large to analyse and clean by Excel. Therefore, BigQuery SQL was used.
* To get visuals onto for the Share part of this project, the dailyActivity_merged CSV file was uploaded onto Tableau. 

### Clean
#### dailyActivity_merged
* When trying to upload into Big Query, there was an error with dailyActivity_merged, as all dates could not be parsed as a TIMESTAMP.
* After some research, this problem was solved by changing the format of the ActivityDate column.
* Checking for NULLs in dailyActivity_merged:

![image](https://user-images.githubusercontent.com/70644015/221353831-857a78f6-f86c-4995-9679-a6bb426d219c.png)

* Checking other errors for every column. TotalDistance is in the below image, but this was done for every column. No errors came to light.

![image](https://github.com/GrossG/Bellabeat_Case_Study/assets/70644015/f0161b67-dc32-46d0-8656-b44bec333223)

* Checking numerical values to see if any were less than zero was checked by data filtering in Excel

![image](https://user-images.githubusercontent.com/70644015/221354356-e69bd06c-3e85-4c50-bf3e-165fc30fd571.png)

* To provide an analysis of the weekdays, a new column needed to be derived from the dates provided. This was done using the TEXT() function on Excel.  

![image](https://user-images.githubusercontent.com/70644015/221354578-00db189c-7bc0-49f3-9298-a89fa78fbff0.png)

* An extra column was created in the hourlyCalories_merged file in order to split the day between morning, afternoon and evening

![image](https://user-images.githubusercontent.com/70644015/223092786-8cb27a4f-870f-465e-b370-bf8091b43d13.png)

#### hourssteps_merged
* In order to look at the correlation between steps taken and daily calories, the time and the date need to be split. Below, column C was created to derive the time from the cells in column B via the formula:

![image](https://user-images.githubusercontent.com/70644015/231221659-2f6c34d7-34ae-4366-b4ce-f4db7a2d1d29.png)


### Issues
* April dates in dailyActivity_merged are not recognised as dates in the CSV files, causing an issue when uploading it to BigQuery.
* None of the files have a big enough sample size to provide accurate insights into all FitBit users, with dailyActivity_merged file is the only file with over 30 users

![image](https://github.com/GrossG/Bellabeat_Case_Study/assets/70644015/82643e97-26b2-4582-af40-25a7474ba48d)

## Analyse
Although 10,000 steps a day is recommended, most users' medians have fallen under that mark, with a total median for the users being just under 8,000 steps.

![image](https://user-images.githubusercontent.com/70644015/219617032-654ee6de-81d9-4e12-bf2f-f79a7c0847f8.png)

Sedentary minutes at 82% (932k out of 1.1m minutes logged) is by far the highest type of activity.

![image](https://github.com/GrossG/Bellabeat_Case_Study/assets/70644015/8ca88976-f9f3-46a8-957a-73979705c777)

When looking at the fairly active and very active categories, there are a couple of takeaways.

According to the [World Health Organisation](https://www.who.int/news-room/fact-sheets/detail/physical-activity), adults should do at least 150–300 fairly active minutes per week (21-43 minutes daily) and at least 75-150 very active minutes per week (11-21 minutes daily) of physical activity. The bar chart below shows respondents on average doing significantly less fairly active minutes than recommended.

![image](https://github.com/GrossG/Bellabeat_Case_Study/assets/70644015/f6c6a946-d761-402f-9da7-3b8397736705)

There's better news with very active minutes, with the average being above the recommended minutes.

![image](https://github.com/GrossG/Bellabeat_Case_Study/assets/70644015/9e949be1-995c-4f43-92a5-effe9fd0fa64)

## Share

The bar chart below was created using Tableau. This tells us when users logged onto the app the most during the week, with a noticeably higher portion logging on from Tuesday to Thursday. 

![image](https://user-images.githubusercontent.com/70644015/219111957-abe84eed-63be-41e9-8d07-8d5e4e093338.png)

Within these days, users logged onto the app mostly at the start of the day, followed by the evening time

![image](https://user-images.githubusercontent.com/70644015/234617798-34afdf96-1dbd-48da-8a29-69befa8fc572.png)

This usage is consistent throughout the week; users log on more often in the mornings no matter what weekday it is

![image](https://user-images.githubusercontent.com/70644015/234619953-ec16dcfc-be5a-4f57-a747-1ba6fbbe597e.png)

Consistent with data above, Tuesday's log of very active mintues is slightly higher. This is the same across the board

![image](https://github.com/GrossG/Bellabeat_Case_Study/assets/70644015/93eae69a-fcfc-4967-b0f9-5d9d51dda7dc)


## Act

To provide recommendations to the company the original questions need to be addressed. 

### 1. What are some trends in smart device usage?
Most activity was midweek, with users logging on in the mornings. 

Tuesdays was the most popular weekday with every activity type across the board i.e. very active, fairly active etcetra.

### 2. How could these trends apply to Bellabeat customers?

These trends can reveal to Bellabeat users what their training habits are and how they compare to what is recommended for those who take their exercise seriously. 

### 3. How could these trends help influence Bellabeat marketing strategy?

Using different avenues of advertising can help keep brand recognition high, but perhaps focusing advertising of print, television and radio between Friday and Monday could encourage increased use of the app in this timeframe. 

### Marketing recommendation:

The data used in this study is unreliable due to the size and lack of recency. Data on more subjects that's up-to-date should be used when driving marketing recommendations. In saying this, the following is based on the data provided for this case study. 


* To address the lack of daily steps and fairly active minutes, the app should post local trails to encourage the users to engage in more hiking and walking; particularly on the weekends. Users can give a star rating out of 5 to motivate users to try out the best trails in their locality. 
* Subscribers can gift a free month to someone every month. This is basically a free trail but directly recommended from someone you know.
* To keep current users motivated, a wellbeing survey can be given to them where they rate themselves 1-10. One year later, they answer the same survey. If results are not improved from the previous year, recommendations can be given.  
