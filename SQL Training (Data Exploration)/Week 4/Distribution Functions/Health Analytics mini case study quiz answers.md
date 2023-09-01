debugged scripts
•	1.
How many unique users exist in the logs dataset?
________________________________________
SELECT
  COUNT(DISTINCT id)
FROM health.user_logs;
•	2.
How many total measurements do we have per user on average rounded to the nearest integer?
________________________________________
-- for questions 2-8 we created a temporary table
DROP TABLE IF EXISTS user_measure_count;
CREATE TEMP TABLE user_measure_count AS
SELECT
    id,
    COUNT(*) AS measure_count,
    COUNT(DISTINCT measure) as unique_measures
  FROM health.user_logs
  GROUP BY 1; 
-- 2. How many total measurements do we have per user on average?
SELECT
  ROUND(AVG(measure_count)) AS average_value
FROM user_measure_count;
•	3.
What about the median number of measurements per user?
________________________________________
-- 3. What about the median number of measurements per user?
SELECT
  PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY measure_count) AS median_value
FROM user_measure_count;
•	4.
How many users have 3 or more measurements?
________________________________________
-- 4. How many users have 3 or more measurements?
SELECT
  COUNT(*)
FROM user_measure_count
WHERE measure_count >= 3;
•	5.
How many users have 1,000 or more measurements?
________________________________________
-- 5. How many users have 1,000 or more measurements?
SELECT
  COUNT(*)
FROM user_measure_count
WHERE measure_count >= 1000;
•	6.
How many users have logged blood glucose measurements?
________________________________________
-- 6. Have only logged blood glucose measurements?
SELECT
  COUNT(DISTINCT id)
FROM health.user_logs
WHERE measure = 'blood_glucose';
•	7.
How many users have at least 2 types of measurements?
________________________________________
-- 7. Have at least 2 types of measurements?
SELECT
  COUNT(*)
FROM user_measure_count
WHERE unique_measures >= 2;
•	8.
How many users have all 3 measures - blood glucose, weight and blood pressure?
________________________________________
-- 8. Have all 3 measures - blood glucose, weight and blood pressure?
SELECT
  COUNT(*)
FROM user_measure_count
WHERE unique_measures = 3;
•	9.
For users that have blood pressure measurements, what is the median systolic/diastolic blood pressure values?
________________________________________
-- 9.  What is the median systolic/diastolic blood pressure values?
SELECT
  PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY systolic) AS median_systolic,
  PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY diastolic) AS median_diastolic
FROM health.user_logs
WHERE measure = 'blood_pressure';

