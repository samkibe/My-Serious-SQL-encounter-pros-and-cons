Using Health analytics Data
#### Weight summary STATS SQL
- SELECT 
- ROUND(MIN(measure_value), 2 )AS min_weight,
- ROUND(MAX(measure_value), 2) AS max_weight,
- 
- ROUND(VARIANCE(measure_value),2) AS variance_weight,
- ROUND(STDDEV(measure_value),2) AS stddev_weight
