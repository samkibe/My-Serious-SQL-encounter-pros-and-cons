### APPLIED STATS
#### Central Tendacy (fro statistics 101)
- Mean/Average (Arithmetic mean - SUM(Total)/number of values
- Medium (50th percentile, finding the middle value)
- Mode (most frequent value/value that appears the most/common value/value with the highest occurences)

What is the average measure_value? below are our 'measure types' in our dataset , 'health analytics data' AND to figure out averag, we are going to use 'GROUP BY'
- blood glucose
- blood pressure
- weight

THEN INSPECT THEM 

example sequel for measure inspections
- SELECT
 measure,
 - AVG(measure_value) AS avg_measure_value
- FROM
  health.user_logs
- GROUP BY
 measure;
 
 ### SQL IMPLMENTATION FOR AVG/MEAN MEDIAN & MODE copy & paste no need to think so much about it
 1. for AVG/MEAN
 - AVG(example_values) AS mean_value
 2. for MEDIUM c&p
 - PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY example_values) AS medium_value
 3. for MODE
 - MODE() WITHIN GROUP (ORDER BY example_values) AS mode_value
 
 #### in code for measure
- SELECT
 measure,
- { AVG(measure_value) AS avg_measure_value }
- { PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY measure_value) AS medium_value }
- { MODE() WITHIN GROUP (ORDER BY measure_value) AS mode_value }
- FROM
  health.user_logs
- GROUP BY
 measure;
 
 #### in code for weight in 'kilos'
- SELECT
- AVG(measure_value) AS avg_weight,
- PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY measure_value) AS medium_weight,
- MODE() WITHIN GROUP (ORDER BY measure_value) AS mode_weight
- FROM
  health.user_logs
- HERE measure = 'weight';
  
  
