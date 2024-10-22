# Bike-sales

## Table of content

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Recommendations](#recommendations)
  ### Project Overview
  ---
  This data analysis project aims at providing insights into the sales performances of a bike company over past sales, by analyzing various aspects that can affect the purchase of bikes using the data set, we seek to identify trends that can improve the sales of bikes and make recommendations for decisions in the future.
![Bike-Purchased-Sales-Dashboard](https://github.com/Pioneer-007/Bike-sales/blob/fbec686210b12d8307553ca389f362e4fcbaecc2/BIKE%20PURCHASED.png)



### **Data Sources**

This primary dataset used for this analysis is the [bikes dataset](https://github.com/Pioneer-007/Bike-sales/blob/f9a67f0be53cf46282c680d75428b77c5c5fffb6/bikes.xlsx),it contains detailed information about the sales of bike of a company.

### *Tools*
- Excel -Data Cleaning
  - [Download Here](https://microsoft.com)
- Power BI -Data Visualization
  - [Download Here](https://microsoft.com)

  ### Data cleaning and preparation
  In the initial data preparation phrase ,we performed the following tasks:
  1. Data loading and Inspecting.
  2. Removal of duplicate.
  3. Handling of missing values.
  4. Data cleaning and formatting.
 

### Exploratory Data Analysis
1. what is the total bikes puchased?
2. Is the sales of bikes affected by gender?
3. Is the sales of bikes affected by occupation?
4. Is the sales of bikes affected by marital status?
5. Does age affect the purchase of bike?
6. Does the commute distance affect the purchase of bikes?
7. Does income and education affect the purchase of bikes?
8. Does Marital status and region affect the purchase of bike?


### Data Analysis
The data analysis was done using:
1. Excel
2. Power BI
3. SQL
```SQL
Select * from bike_buyers$ 

with duplicate_CTE as (
select ID,[Marital Status],Gender,Income,Children,Education,Occupation,[Home Owner],
Cars,[Commute Distance],Region,Age,[Purchased Bike],row_number() over (partition by ID,[Marital Status],Gender,Income,Children,
Education,Occupation,[Home Owner],Cars,[Commute Distance],Region,Age,[Purchased Bike] order by ID)AS DUPCOUNT FROM bike_buyers$
)
delete from duplicate_CTE WHERE DUPCOUNT > 1

1 select COUNT(ID) AS Total_bikes from bike_buyers$

2 select [Purchased Bike],SUM(CASE when Gender = 'M' THEN 1 else 0 end) as Males,SUM(CASE when Gender = 'F' THEN 1 else 0 end)AS
Females from bike_buyers$ group by [Purchased Bike]

3 select SUM(CASE when Occupation = 'Skilled Manual' THEN 1 else 0 end) as [skilled manual],SUM(CASE when Occupation = 'Professional' THEN 1 else 0 end)AS
Professional,sum(CASE when Occupation='Clerical' then 1 else 0 end)as Clerical,sum(CASE WHEN Occupation='Manual' then 1 else 0 end)as Manual,
sum(CASE when Occupation = 'Management' then 1 else 0 end)as management from bike_buyers$ 

4 select [Purchased Bike],SUM(CASE when [Marital Status] = 'M' THEN 1 else 0 end) as Married,SUM(CASE when [Marital Status] = 'S' THEN 1 else 0 end)AS
Single from bike_buyers$ group by [Purchased Bike]

5 select SUM(CASE when Age < 30 THEN 1 else 0 end) as young ,SUM(CASE when Age between 30 and 45 THEN 1 else 0 end)AS Adult
,sum(CASE when Age >45  then 1 else 0 end)as old from bike_buyers$

 6 select [Purchased Bike],SUM(CASE when [Commute Distance] = '0-1 Miles' THEN 1 else 0 end) AS [0-1 Miles],SUM(CASE when [Commute Distance] = '1-2 Miles' THEN 1 else 0 end)AS [1-2 Miles], Sum(CASE when [Commute Distance]= '2-5 Miles' then 1 else 0 end) as [2-5 Miles], SUM(CASE when [Commute Distance] = '5-10 Miles' then 1 else 0 end)
 As [5-10 Miles], SUM(CASE when [Commute Distance]='10+ Miles' then 1 else 0 end) as [10+ Miles] from bike_buyers$ group by [Purchased Bike]
  
 7 select Education,sum(Income) as income from bike_buyers$ Group by Education order by income

 8  select [Purchased Bike],[Marital Status],sum(CASE WHEN Region = 'Europe' then 1 else 0 end) as europe , sum(CASE WHEN Region = 'Pacific' then 1 else 0 end) as 
  Pacific, sum(CASE when Region = 'North America' then 1 else 0 end ) as [North America]from bike_buyers$ group by [Purchased Bike],[Marital Status]

```


### Result and Findings.
 There was a total of 1000 bikes purchased.The males especially adolescent purchased more bikes than females,the males were professional and skilled manual workers and have a commute distance of 0-1 miles with a bachaelors degree and followed by those with partial colleges.

 ### Recommendations
 The Bike sales should advertise more to adolescent males that are married and females that are single who are professional and skilled manual workers that have commute distances of 0-1 miles .

 😄
 
 🚴‍♂️
 
 `thank_you`
