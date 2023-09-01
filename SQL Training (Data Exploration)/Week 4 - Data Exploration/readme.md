Using Health analytics Data
#### Weight summary STATS SQL
- SELECT
- ROUND(MIN(measure_value), 2) AS min_weight,
- ROUND(MAX(measure_value), 2) AS max_weight,
- ROUND(AVG(measure_value), 2) AS avg_weight,
- [CAST(PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY measure_value) AS NUMERIC), 2) AS median_value]
- [CAST(PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY measure_value) AS NUMERIC), 2) AS median_weight] no cleat some error at AS
- ROUND(MODE() WITHIN GROUP (ORDER BY measure_value), 2) AS mode_weight,
- ROUND(VARIANCE(measure_value),2) AS variance_weight,
- ROUND(STDDEV(measure_value),2) AS stddev_weight
- FROM health.user_logs
- WHERE measure = 'weight'
- AND measure_value BETWEEN 1 AND 201;

### CAST at Median fuction is used to convert float the output to NUMERIC
EXAMPLE FIND MEDIAN?
- CAST(PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY measure_value) AS NUMERIC), 2) AS median_value]
