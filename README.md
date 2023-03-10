# Bellabeat_Case_Study

## Background
Bellabeat, a hightech manufacturer of smart health-focused products for women, was founded in 2013 by Urška Sršen and Sando Mur. This technology design was designed by Sršen's background as an artist. 

Bellabeat had devolved a worldwide presence by 2016, and although focusining on digital marketing, has also invested in many traditional avenues of advertisting; radio, billboards, print, and television.

To get to the next level, Sršen knows the importance of utilising available consumer data; asking the marketing analytics team to analyse usage data of their products. High-level recommendations are hoped to come from this, which can shape Bellabeat's marketing strategy. 


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

## Process
### Upload
* I downloaded the above data from Kaggle onto my computer; the 18 CSV files.
* Some files were far too large to analyse and clean by Excel. Therefore, BigQuery SQL was used.
* To get visuals onto for the Share part of this project, the dailyActivity_merged CSV file was uploaded onto Tableau. 

### Clean
* When trying to upload into Big Query, there was an error with dailyActivity_merged, as all dates could not be parsed as a TIMESTAMP.
* After some research, this problem was solved by changing the format of the ActivityDate column.
* Checking for NULLs in dailyActivity_merged:

![image](https://user-images.githubusercontent.com/70644015/221353831-857a78f6-f86c-4995-9679-a6bb426d219c.png)

* Checking other errors for every column. TotalDistance is in the below image, but this was done for every column. No errors came to light.

![image](https://user-images.githubusercontent.com/70644015/221354765-539fcb4b-5a0f-4266-a9e2-8ea7c9ed8471.png)

* Checking numerical values to see if any were less than zero was checked by data filtering in Excel

![image](https://user-images.githubusercontent.com/70644015/221354356-e69bd06c-3e85-4c50-bf3e-165fc30fd571.png)

* To provide an analysis of the weekdays, a new column needed to be derived from the dates provided. This was done using the TEXT() function on Excel.  

![image](https://user-images.githubusercontent.com/70644015/221354578-00db189c-7bc0-49f3-9298-a89fa78fbff0.png)

* An extra column was created in the hourlyCalories_merged file in order to split the day between morning, afternoon and evening

![image](https://user-images.githubusercontent.com/70644015/223092786-8cb27a4f-870f-465e-b370-bf8091b43d13.png)


### Issues
* April dates in dailyActivity_merged are not recognised as dates in the CSV files, causing an issue when uploading it to BigQuery.
* None of the files have a big enough sample size to provide accurate insights into all FitBit users, with dailyActivity_merged file is the only file with over 30 users

![image](https://user-images.githubusercontent.com/70644015/219110913-4ea6c556-5ee8-4d74-838e-f3c4cee6296f.png)

## Analyse
Although 10,000 steps a day is recommended, most users' medians have fallen under that mark, with a total median for the users being just under 8,000 steps.

![image](https://user-images.githubusercontent.com/70644015/219617032-654ee6de-81d9-4e12-bf2f-f79a7c0847f8.png)

## Share

The bar chart below was created using Tableau. This tells us users logged onto the app the most during the week, with a noticable decrease from Friday to Monday. 

![image](https://user-images.githubusercontent.com/70644015/219111957-abe84eed-63be-41e9-8d07-8d5e4e093338.png)



