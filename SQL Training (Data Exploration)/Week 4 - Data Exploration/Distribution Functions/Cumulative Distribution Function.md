## Data Algorithmn for a CDF
- Sort values ascending
- assign 1-100 percentile
- for each (GROUP BY) PERCENTILE To calc floor& ceiling values, and record (FOR EACH always asks for GROUP BY)
- ALL Window functions are analytical fuctions, but not all aqnalytical fuunctions are window functions.
- Analytical fuctions are the larger set where window functions exist
- Window fuctions are a subset of analytical functions

## EXAMPLE of analytical functions
- NTILE(1OO) IS THE NUMBER OF BACKETS OR BLOCKS YOU WANT TO SPLIT YOUR DATA INTO.
- NTILE(10/100) OVER (ORDER  BY measure_value) AS percentile
### algorithmn
- ( SELECT measure_value,
- NTILE(100) OVER (ORDER  BY measure_value) AS percentile
- FROM health.user_logs
- WHERE measure = 'weight';) this code is working

Cummulative Distribution function has ;- TO CALCULATE AGGREGATES
- A CTE and inside A cte we have an NTILE(100) OR CUME_DIST
- Then an aggregate function with MIN, MAX and COUNT
  
### code snippet as below :- and it is working on Health data

- WITH percentile_values AS (   ### a cte
- SELECT measure_value,
- NTILE(100) OVER (ORDER  BY measure_value) AS percentile
- FROM health.user_logs
- WHERE measure = 'weight'
- )
- SELECT
- percentile,
- MIN(measure_value) AS floor_value,
- MAX(measure_value) AS ceiling_value,
- COUNT(*) AS percentile_counts
- FROM percentile_values
- GROUP BY percentile
- ORDER BY percentile;
  
# OR
- DROP TABLE IF EXISTS clean_weight_logs;
  ### removing outliers using a temp teble
- CREATE TEMP TABLE clean_weight_logs AS (
- SELECT *
- FROM health.user_logs
- WHERE measure = 'weight'
- AND measure_value BETWEEN 1 AND 201
- );
- WITH percentile_values AS (   
- SELECT measure_value,
- NTILE(100) OVER (ORDER  BY measure_value) AS percentile
- FROM 
- WHERE measure = 'weight'
- )
- SELECT
- percentile,
- MIN(measure_value) AS floor_value,
- MAX(measure_value) AS ceiling_value,
- COUNT(*) AS percentile_counts
- FROM percentile_values
- GROUP BY percentile
- ORDER BY percentile;

### Frequency distribution 
- find min, max boundaries values
- split into N equal backets by values
- for each backet a. cal avg values & record count

### code
  - SELECT
  - WIDTH_BUCKET (measure_value, 0, 200, 50)
  - AVG(measure_value) AS measure_value,
  - COUNT (*) AS frequency
  - FROM clean_weight_logs / health.user_logs
  - GROUP BY bucket
  - ORDER BY bucket
