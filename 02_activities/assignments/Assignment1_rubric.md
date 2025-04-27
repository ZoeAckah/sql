# Assignment 1: Meet the farmersmarket.db and Basic SQL

## General
  - Weight: *30 points*
  - Criteria: Zoe Ackah
  - Criteria: Assignment is free of noticeable typos
  - Criteria: One Logical Model exists
    - cannot be a duplicate of my example tables from Session 1 slides
  - Criteria: assignment1.sql is completed
  - Criteria: assignment1.sql is correct

## Section 1
Welcome to Zoe Ackah's First SQL Assignment 
### Prompt 1
- Two tables are diagramed as a logical model
  - Needs to contain table names, column names, relationships between columns, relationship-type
- Any format acceptable so long as a "logical model"

## Section 2
 **First Attempt:** 
--Who came out on a rainy or snowy day? I kind or wrote this myself but GitHub Copilot had to help me
SELECT 
    market_date_info.market_date,
    market_date_info.market_rain_flag,
    market_date_info.market_snow_flag,
    customer.customer_id,
	customer.customer_first_name,
	customer.customer_last_name
 
FROM 
    market_date_info
JOIN 
    customer_purchases
ON 
    market_date_info.market_date = customer_purchases.market_date
JOIN 
    customer
ON 
    customer_purchases.customer_id = customer.customer_id
WHERE 
    market_date_info.market_rain_flag = 1 OR market_date_info.market_snow_flag = 1;
- **Second Attempt:** 

--who came out on a rainy or day?? The problem is the actually snowy day purchase are zero. (Thankyou GitHub CoPilot - otherwise this would have been impossible)
SELECT 
    customer.customer_first_name,
    customer.customer_last_name,
    COUNT(*) AS rainy_snowy_visit_count
FROM 
    market_date_info
JOIN 
    customer_purchases
ON 
    market_date_info.market_date = customer_purchases.market_date
JOIN 
    customer
ON 
    customer_purchases.customer_id = customer.customer_id
WHERE 
    market_date_info.market_rain_flag = 1 
    or market_date_info.market_snow_flag = 1
GROUP BY 
    customer.customer_id, 
    customer.customer_first_name, 
    customer.customer_last_name
ORDER BY 
    rainy_snowy_visit_count DESC; 

## Section 3
- **All questions have been attempted** 
- **The following questions return the correct result set:** 
  - AGGREGATE, Question 2
  - DATE, Question 2

## Criteria

|Criteria|Complete|Partial|Incomplete|
|--------|----|----|----|
|Section 1, Prompt 1 Requirements|All requirements are met.|Missing some requirements.|Several requirements are not met or diagram is not a logical model.|
|Section 2 Requirements|All requirements are met and result sets are correct.|Some questions missing or wrong result set.|Several questions missing.|
|Section 3 Requirements|All requirements are met and result sets are correct.|Some questions missing or wrong result set.|Several questions missing.|
