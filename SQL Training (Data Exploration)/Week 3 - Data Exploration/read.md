### We will be using Health analytics data

#### hack - shift + enter automaticlly formats sequel on sql pad
#### USE ROUND when rounding off to lesser decimal point of your requirement

EXAMPLE CODE SNIPPET to investigate measure in our dataset 'HEALTH ANALYTICS DATA' :-
##### 1
- SELECT * FROM health.user_logs

##### 2
- SELECT * FROM health.user_logs
- LIMIT 10;

##### 3
- SELECT measure_value FROM health.user_logs
- LIMIT 10;

##### 4
- SELECT measure_value FROM health.user_logs
- WHERE measure = 'weight'
- LIMIT 10;
