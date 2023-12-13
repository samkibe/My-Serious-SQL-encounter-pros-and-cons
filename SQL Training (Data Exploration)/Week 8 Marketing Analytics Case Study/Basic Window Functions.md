#### WINDOW function algorithm
- CALCULATION (SUM,MAX,AVG, AGGREGATE FUNCTION(inputs, nos, )
- OVER -Window frame- (
- PARTIOTION BY -- outputs one record per row / % of total frequences
- ORDER BY-- ensure precalculated, -- shows in the order the darta appears
- FRAME CLAUSE -- separate groups
- )
- ![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/6d806ef4-f967-4361-9ec8-aac1a4e9fe49)


### Difference between GROUP BY and PARTITION BY in the context of window function.
  
- Questions answered what is an aggregate GROUP BY function and a WINDOW FUNCTION
- ![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/8676cdcf-0518-4464-a081-df15144f10e8)

###  Partition By 2 Columns
-  ![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/7032fb44-e020-4da8-97be-07d8c4382696)

###  Multiple Level Partition By
- ![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/78399f31-1cc6-4471-a002-1759fc97b694)
  
### Multiple calculation window functions eg sum, avg, rank, dense rank, max et cetera
- ![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/20da3c4c-7ab7-4a5c-861a-47063ef43211)

### Blank/ Empty or Missing Partition By question like -- what is the sum of sales per custo mer and their % of total sales? (per customer)
- 1st function - Sum (sales) over/ partition by customer_id -- AS customer sales
- 2nd function Sum(sales) over (empty) AS TOTALS SALES
- to calculate the % per customer we divide the output of 1st function by the output of the second function
- sample code
- SELECT measure, COUNT(*) AS frequency ROUND (100 * COUNT(*) SUM(COUNT(*)) OVER (),  2  ) AS percentage
- FROM health.user_logs GROUP BY measure ORDER BY frequency DESC
- select customer_id sum(sale) over () from customer_sales group by customer_id
  
### SQL ORDER OF OPERATION / SQL Logical Execution Order

- In a nutshell - all SQL queries are “ran” in the following order: VERY IMPOPRTANT, IT HAS BEEN DISCUSSED WIDELY IN THE WEEK 8 TUTORIAL

-- FROM
-- WHERE filters
-- ON table join conditions
-- GROUP BY
-- SELECT aggregate function calculations
-- HAVING
-- Window functions
-- ORDER BY
-- LIMIT
### OR 
-- FROM
-- WHERE filters
-- ON table join conditions
-- GROUP BY
-- SELECT statements
---- Derived column expressions
---- Aggregate functions
-- HAVING
-- Window functions
-- ORDER BY
-- LIMIT
### Ordered Window Functions
-  ![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/b0c433eb-807a-4ed4-8127-62c67fa2ca92)

- ![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/59d39edc-dd0e-4c70-869c-08e5efe1a3e4)

- 

