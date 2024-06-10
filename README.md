# **PWC Call Center Trend Analysis using Power BI**

![pexels-yankrukov-8867482](https://github.com/tanvi19-k/PWC-Analysis/assets/172184420/316b3480-ad77-42c0-a611-b28ac03e4f61)


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

![image](https://github.com/tanvi19-k/PWC-Analysis/assets/172184420/7e7474ba-7504-40a3-a334-d9fd1ee3af13)



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

![image](https://github.com/tanvi19-k/PWC-Analysis/assets/172184420/116a3644-05b4-49f1-879c-c062b6405e2d)


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

![image](https://github.com/tanvi19-k/PWC-Analysis/assets/172184420/3257e0a8-cb37-49de-8f6d-f6185140e72c)


## Insights
  - Based on overall calls :
      - Total calls are `5000`. 
      - Overall `maximum calls` are recorded in the month of *January*.
      - The percentage of issue resolved in *January* was `maximum`, `slightly dip` in *February* then again `increased` in *March*.
      - Most of the calls come in the morning.
      - Majority of the calls are related to *Streaming* issue.
      - *Jim* attended and resolved `maximum calls` than other agents.
   
  - Based on overall satisfaction rating :
      - The average satisfaction rating is `3.4`.
      - Average satisfaction rating decreased over months. *January* has `highest` and *March* has `lowest`.
      - *Martha* got the `highest` satisfaction rating and *Joe* got the `lowest` rating.

  - Based on overall speed of answering calls in seconds :
      - The average speed of answering calls in sec is `67.52`.
      - *Joe's* speed of answering calls is the `highest` and *Becky's* speed is the `lowest` one.

  </br>

***Top 3 agents based on calls attended*** :
  - *Jim*, *Martha*, for 3rd position there are 2 agents *Dan* and *Diane*.
    
      
***Top 3 agents based on calls resolved*** :
  - *Jim*, *Dan*, *Becky*. As we can see *Martha* and *Diane* `attended the maximum calls` than *Becky*, as *Becky* `resolved the maximum calls`.
      
***Top 3 agents based on satisfaction ratings*** : 
  - *Martha*, *Dan*, *Diane*. Even if *Jim* and *Becky* `resolved the maximum calls` they got `lowest satisfaction ratings`.
