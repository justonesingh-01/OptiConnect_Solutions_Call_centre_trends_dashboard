# OptiConnect_Solutions_Call_centre_trends_dashboard
<img width="1536" height="1024" alt="Photo" src="https://github.com/user-attachments/assets/0f59a8cd-480c-4817-ab6d-af6955973cdc" />

## Table of Contents :
-  [Problem statement](#problem-statement)
-  [Data Source](#data-source)
-  [Data Preparation](#data-preparation)
-  [Data Modelling](#data-modelling)
-  [Data Analysis(DAX)](#data-analysis(dax))
-  [Data Visualization Dashboard](#data-visualization-dashboard)
-  [Insights](#insights)

## Problem statement :
In this project Create a dashboard in Power BI for the call center manager that reflects all relevant Key Performance Indicators (KPIs) and metrics in the dataset.

Possible KPIs include (but not limited to):
-  Overall customer satisfaction
-  Overall calls answered/unanswered
-  Total calls handle by Department
-  Average speed of answer
-  Agent’s performance -> average handle time (talk duration) vs calls answered

## Data Source :
Dataset used for this task was presented by [PW-Skills](#pw-skills).

**Dataset:** [Call Centre Dataset](./Call%20Centre%20Dataset.xlsx)

## Data Preparation :
Completed the Data transformation in Power Query and the dataset loaded into Microsoft Power BI Desktop for modeling.

Call Centre Trends dataset is give table named:
-  **`Call Center trends dataset`** which has **`10 columns and 1772 rows`** of observation

Data Cleaning for the dataset was done in the power query editor as follows:

-  Removed Unnecessary data
-  Handle null
-  Each of the columns in the table were validated to have the correct data type

## Data Modelling :
The dataset was cleaned and transformed, it was ready to the data modeled.
-  the **`measure table`** and **`call centre trends dataset`** tables as show below :-
  
<img width="943" height="540" alt="Screenshot 2025-08-12 020010" src="https://github.com/user-attachments/assets/c0c34d22-59a5-4b95-aa36-9cca09af531c" />

## Data Analysis (DAX) :
Measures used in all visualization are:

-  Average speed of answered = **`AVERAGE('Dataset'[Speed of answer])`**

-  Average of Satisfaction = **`AVERAGE('Dataset'[Satisfaction rating])`**

-  Count of Satisfaction rating = **`COUNT('Dataset'[Satisfaction rating])`**

-  Overall Customer Satisfaction = **`DIVIDE([Positive Satisfaction Rating],[Count of Satisfaction rating],0)`**

-  Positive Satisfation Rating = **`CALCULATE(COUNT('Dataset'[Satisfaction rating]),FILTER('Dataset','Dataset'[Satisfaction rating] IN {4,5}))`**

-  Resolved calls = **`COUNTX(FILTER('Dataset','Dataset'[Resolved] = "Y"), 'Dataset'[Resolved])`**

-  Unresolved calls = **`COUNTX(FILTER('Dataset','Dataset'[Resolved] = "N"), 'Dataset'[Resolved])`**

-  Total Calls Answered = **`COUNTX(FILTER('Dataset','Dataset'[Answered (Y/N)] = "Y"),'Dataset'[Answered (Y/N)])`**

-  Total Calls Uanswered = **`COUNTX(FILTER('Dataset','Dataset'[Answered (Y/N)] = "N"), 'Dataset'[Answered (Y/N)])`**

-  Total Calls = **`CALCULATE('Table'[Total Calls Answered] + 'Table'[Total Calls Unanswered])`**

## Data Visualization Dashboard :
Data visualization for the data analysis (DAX) was done in Microsoft Power BI Desktop.

Shows visualizations from Call Center Trends :
<h1 align="center">Call Centre Trends (Overview)</h1>

<img width="1475" height="734" alt="Screenshot 2025-08-12 015259" src="https://github.com/user-attachments/assets/c5823d91-9621-4976-a08f-aafee0945fd6" />


<h1 align="center">Call Centre Trends (Agent's Performance)</h1>

<img width="1305" height="734" alt="Screenshot 2025-08-12 015556" src="https://github.com/user-attachments/assets/6da74bff-5ea0-4583-a754-d641f77dd014" />

## Insights :

-  Most of the satisfaction ratings from each call are 3 and 4.
-  The average satisfaction rating has fluctuate over the span of time. Date 30th of the month brought the highest satisfaction rating and 20th the lowest.
-  The percentage of issue resolved in 11th was the highest i.e.,84 and with a dip in 21th i.e., 48. It increased again in 30th.
-  The majority of calls come in the Afternoon.
-  The average speed of answer by Joe is the highest.
-  The call resolution rate of Dan is the highest, even though the average speed of his answers is lower compared to Joe. The call answered by him are also higher than the average number of calls answered.
-  Becky's speed of answer is the lowest among all, and her rate of calls resolved is higher. She is in the 5th position in the call resolution rate. 
-  Joe has the highest  speed of answered in the second.
-  Customer Satisfaction seems relatively unaffected by moderate changes in both Speed of Answer and Talk Duration.Even though some agents answered faster or spoke longer,
   average satisfaction scores stayed constant at 3.

