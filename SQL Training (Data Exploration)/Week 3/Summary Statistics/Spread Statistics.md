##### WHAT is the MIN, MAX,  range [MIN - MAX] (body) weights in our Dataset 'Health Analytics data'?

### SQL IMPLMENTATION FOR MAX MIN & RANGE copy & paste no need to think so much about it
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
check how round is used in below examples


