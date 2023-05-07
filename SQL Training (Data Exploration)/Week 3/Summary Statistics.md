#### APPLIED STATS
EXAMPLE CODE SNIPPET to investigate measure in our dataset 'HEALTH ANALYTICS DATA'
- SELECT measure_value FROM health.user_logs
- WHERE measure = 'weight'
- LIMIT 10;

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
  
