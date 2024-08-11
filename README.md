# CUSTOMER CHURN ANALYSIS
## Aim 
## Approach and Analysis
## Metrics used
## Backend
### 1. DAX 
```1DAX
Customer Rank =
RANKX(
    ALL('Customer details'), 
    'Customer details'[Revenue_total],
    ,
    DESC
)
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
## Insights
### Q1
### Q2
### Q3
## Recommendations
