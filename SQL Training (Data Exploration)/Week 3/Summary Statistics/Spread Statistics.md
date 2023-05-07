##### WHAT is the MIN, MAX,  range [MIN - MAX] (body) weights in our Dataset 'Health Analytics data'?

### SQL IMPLMENTATION FOR MAX MIN & RANGE copy & paste no need to think so much about it
1. for MAX
 - MAX(example_values) AS max_value
2. for MIN
 - MIN(example_values) AS min_value
3. for RANGE
 - MIN(example_values) - MAX(example_values) AS weight_range
 
example code in our dataset
- SELECT
- MIN(measure_value) AS min_weight,
- MAX(measure_value) AS max_weight,
- MIN(measure_value) - MAX(measure_value) AS weight_range
- FROM
  health.user_logs
- WHERE measure = 'weight';
- AND measure_value >0
- AND measure_value < 200;
- 'OR USE'
- AND measure_value BETWEEN 1 AND 201;

##### Variance & Standard Deviation ALWAY COMPARING SOMETHING WITH THE 'MEAN'
VARIANCE = (STANDARD DEVIATION)SQUARED/ 2
### SQL IMPLMENTATION FOR VARIANCE & STDDEV copy & paste no need to think so much about it
1. for VARIANCE
 - VARIANCE(example_values) AS variance_value
2. for STDDEV
 - STDDEV(example_values) AS std_dev_value

 ## then check how ROUND TO 2 DECIMAL PLACE is used in below examples
- SELECT
- ROUND(VARIANCE(measure_value),2) AS variance_weight,
- ROUND(STDDEV(measure_value),2) AS stddev_weight
- FROM
  health.user_logs
- WHERE measure = 'weight'
- AND measure_value BETWEEN 1 AND 201;


