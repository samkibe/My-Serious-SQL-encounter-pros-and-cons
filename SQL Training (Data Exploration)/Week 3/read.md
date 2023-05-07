##### We will be using Health analytics data
example of sql code snippet to investigate health data include :-
##### 1
- SELECT * FROM health.user_logs

##### 2
- SELECT * FROM health.user_logs
- LIMIT 10;

#### 3
- SELECT measure_value FROM health.user_logs
- LIMIT 10;

#### 4
- SELECT measure_value FROM health.user_logs
- WHERE measure = 'weight'
- LIMIT 10;
