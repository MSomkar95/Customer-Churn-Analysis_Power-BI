# CUSTOMER CHURN ANALYSIS

## Project Overview
The imaginary telecom company faces a grim challenge of increased customer churn rate of approximately 27%, and I aim to utilize Power BI in visualizing the data, design the dashboard and draw the actionable insights by also providing business recommendations that the company could apply which could improve the customer retention.   

## Table of Contents
- [Dataset](#dataset)
- [Approach and Analysis](#approach-and-analysis)
- [Tools used](#tools-used)
- [KPIs used](kpis-used)
- [Backend](backend)
- [Recommendations](recommendations)

## Dataset
[Dataset](https://drive.google.com/drive/folders/18GP3UtiWel1hdVGECHMSxx9X3qQbgI--?usp=drive_link) 

## Approach and Analysis
<img width="705" alt="chart" src="https://github.com/user-attachments/assets/cc8ef101-a28c-4480-a5c6-969dc374c1e3">

## Tools used
- MS Excel: for data cleaning
- Power BI: for data visualization

## KPIs used
- Total Churned customers
- Churn Rate
- Customer Rank

  <img width="869" alt="High value group" src="https://github.com/user-attachments/assets/64f87ff5-4d74-40e0-a511-f77385f59727">
  
- Revenue Contribution percentage
- Average Revenue Per Customer (ARPU)
- Average Tenure
- Average Monthly Revenue per customer 
- Total Revenue etc

## Backend
### 1. Key DAX measure 
    ````DAX
    
    Customer Value Category =                                                //Classification of customer groups based on the revenue generated
        VAR HighcategoryCOUNT= COUNTROWS('Customer details') * (0.2)        //Top 20% customers
        VAR otherCOUNT= COUNTROWS('Customer details')- HighcategoryCOUNT
        VAR tierCOUNT=  otherCOUNT/3                                            //Rest 80% of customers
        RETURN
            IF('Customer details'[Customer Rank]<= HighcategoryCOUNT,"High-Value customer",
                IF('Customer details'[Customer Rank]<= HighcategoryCOUNT + tierCOUNT,"Potential High-value customer",
                     IF('Customer details'[Customer Rank]<= HighcategoryCOUNT + (2*tierCOUNT), "Medium-Value customer","Low-value customer"
                     )
                )
            )
    
### 2. Power Query (M language)
        ```Power Query
        = Table.AddColumn(#"Filtered Rows3", "Group_months", each if [Tenure in Months] <= 12 then "<1 year" else if [Tenure in Months] <= 24 then "1-2 years" else if [Tenure in Months] <= 36 then "2-3 years" else if [Tenure in Months] <= 48 then "3-4 years" else if [Tenure in Months] <= 60 then "4-5 years" else if [Tenure in Months] <= 72 then "5-6 years" else null)

## Insights

<img width="731" alt="Overall Insights" src="https://github.com/user-attachments/assets/0337616d-993a-4913-9f18-3f049640d9c3">

- Potential-High value group could be nurtured to be the next high-value group, and the only point of concern is the average tenure i.e. 45 months only.
- Among the internet type Fiber optics is preferred only by the High-value group only and the average tenure here is above 5 years, and the total revenue contribution reaped through this service type is 72%.
- Internet-type services are preferred by those customers who spend 2.5 years or more with the company.
- When the above group of customers is clubbed along with the potential high-value group the situation is: 3286 customers (46.6% of customers) are responsible for 85% of the total revenue.
- Priority customer groups to address, 1. High-value customer group, 2. Potential high-value customer group, 3. Customers based out of cities- San Diego and Los Angeles and  4. Age Group of 60 and above, whose average Average Monthly revenue contribution is the highest.
  
<img width="730" alt="High Priority Customer Analysis" src="https://github.com/user-attachments/assets/e247c270-a993-4818-a672-0aa2957fbb27">

- Groups Under Risk:  
   - City: San Diego- Here 58% of the churn rate is accounted for by the Potential High- Value group customers whose average monthly revenue was $100.
   - Customers using paperless billing are more dissatisfied accounting for a 72% churn rate. 
   - By contract: Month-to-month contract is more customer friendly accounting for 51.2% of popularity out of which churn rate is 46% is the churn rate, as services

  <img width="727" alt="Churn Analysis" src="https://github.com/user-attachments/assets/cec0f890-eeb7-4ae0-963c-c817983e9b67">

- The cities San Diego and Los Angeles despite having a comparable number of customers, San Diego impacts a whopping 65% churn and there the retained customers are less than those churned (185 out of 285 churned).
- Market Penetration is low as the city with the highest customer penetration is just above 4%. 
- In San Diego, High-value customers with 49% contribution to the total revenue contribution of the city of which the churned customers have an average tenure of around 5 years. In addition, 82% of churn is because of competitor activity, which means the competitor services are premium and we must upgrade our premium services.
- Customers whose tenure is less than 6 months have a churn rate of a whopping 85%.
- Internet-type services are preferred by those customers who spend 2.5 years or more with the company.
  
  <img width="356" alt="Payments chart" src="https://github.com/user-attachments/assets/f57bad34-2ab8-4443-bd3c-28bba225e0b6">

- Credit card payment option has less churn rate, but less popular when compared to the bank withdrawal type.

### Q1
### Q2
### Q3

## Recommendations
- Competitor activities analysis needs to be done- the strength of their services needs to be analyzed.
- The premium services offered by the company must follow the current trend and upgrade its services as per the demands of High-Value as well as Potential High-value customers (future high-value 
  group).
- Internet-type services especially Fiber optics services need to be marketed targeting the potential high-value customer group.
- An advanced payment method needs to be introduced as even though the bank withdrawal type is highly popular it contributes to a 34% churn rate.


