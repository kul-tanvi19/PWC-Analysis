# **PWC Call Center Trend Analysis using Power BI**

![pexels-yankrukov-8867482](https://github.com/tanvi19-k/PWC-Data-Analysis/assets/172184420/a010ecd5-0440-4805-b7cf-685925369acb)


## Table of Content:
  - [Problem Statement](#Problem-Statement)
  - [Datasource](#Datasource)
  - [Data Preparation](#Data-Preparation)
  - [Data Modeling](#Data-Modeling)
  - [Data Analysis](#Data-Analysis)
  - [Data Visualization](#Data-Visualization)
  - [Insights](#Insights)


## Problem Statement
Create a Power BI dashboard to analyse the trends and patterns of a Call Center that helps manager to reflect all relevant Key Performance Indicators (KPIs) and metrics in the dataset.


**Possible KPIs include (to get you started, but not limited to):**
  - Overall customer satisfaction
  - Overall calls answered/abandoned
  - Calls by time
  - Average speed of answer
  - Agent’s performance quadrant -> average handle time (talk duration) vs calls answered


## Datasource
Dataset was provided by PWC Switzerland.

![image](https://github.com/tanvi19-k/PWC-Data-Analysis/assets/172184420/7148674d-a255-42db-b951-1e7b22c39c5b)


## Data Preparation
  - Understanding the date
      - Data consists of `10 Columns` and `5000 records`.
      - Column names are as `Call Id`, `Agent`, `Date`, `Time`, `Topic`, `Answered (Y/N)`, `Resolved`, `Speed of answer in seconds`, `AvgTalkDuration` and `Satisfaction rating`.

  - Data Transformation
      - Data is then loaded into Power BI to do some transformations.
      - After observing the data I found that the data type of few columns like `Time`, `AvgTalkDuration` and `Satisfaction rating` was incorrect so I changed `Time`, `AvgTalkDuration` data type to `Time` and `Satisfaction rating` to `Int`.
      - Created separate bins for `Time` to analyse call trends as per time parameter.


## Data Modeling
Dataset is cleaned and transformed, now the data is ready for modeling.

![image](https://github.com/tanvi19-k/PWC-Data-Analysis/assets/172184420/25a74bef-acaf-4b6a-b032-b236a44a6fe2)


## Data Analysis
  - DAX measures used :
      - Total Calls = `COUNT('Call Center'[Answered (Y/N)])`.
      - Average satisfaction rating = `AVERAGE('Call Center'[Satisfaction rating])`.
      - Ratings between 4 & 5 = `CALCULATE(COUNTROWS('Call Center'),AND('Call Center'[Satisfaction rating] >= 4, 'Call Center'[Satisfaction rating] <= 5))`.
      - Poor Ratings = `CALCULATE(COUNTROWS('Call Center'),'Call Center'[Satisfaction rating] = 1)`.

  - Filters used :
      - Filter call center report by `Months`.
      - Filter call center report by `Resolved` parameter.
      - Filter call center report by `Topics`.
      - Filter call center report by `Agents`.

## Data Visualization
**Dashboard**

![image](https://github.com/tanvi19-k/PWC-Data-Analysis/assets/172184420/4d50ce68-406b-4959-a011-fee16539f429)


## Insights
