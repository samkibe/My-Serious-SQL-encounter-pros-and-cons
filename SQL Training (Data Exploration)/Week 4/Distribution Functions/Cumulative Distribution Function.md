## Data Algorith for a CDF
- Sort values ascending
- assign 1-100 percentile
- for each (GROUP BY) PERCENTILE To calc floor& ceiling values, and record (FOR EACH always asks for GROUP BY)
- ALL Window functions are analytical fuctions, but not all aqnalytical fuunctions are window functions.
- Analytical fuctions are the larger set where window functions exist
- Window fuctions are a subset of analytical functions

## EXAMPLE of analytical functions
- NTILE(1OO) IS THE NUMBER OF BACKETS OR BLOCKS YOU WANT TO SPLIT YOUR DATA INTO.
- NTILE(10/100) OVER (ORDER  BY measure_value) AS percentile

- SELECT measure_value,
- NTILE(100) OVER (ORDER  BY measure_value) AS percentile
- FROM health.user_logs
- WHERE measure = 'weight';

Cummulative Distribution function has ;- TO CALCULATE AGGREGATES
- A CTE and inside A cte we have an NTILE(100) OR CUME_DIST
- Then an aggregate function with MIN, MAX and COUNT
