### We will be using Health analytics data
example of sql code snippets to investigate health data include :-
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

### Central Tendacy (fro statistics 101)
- Mean/Average (Arithmetic mean - SUM(Total)/number of values
- Medium (50th percentile, finding the middle value)
- Mode (most frequent value/value that appears the most)
