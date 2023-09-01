### QUESTIONS
#### 1. How can we identify duplicates?
IDENTIFICATION OF DUPLICATES
- Row counts vs distinct row counts (select distinct *)
example 
- SELECT COUNT (*) FROM health.user_logs;

#### 2. Should we remove all of them NO - apply DISTINCT to wipe, although inspect data first
#### 3. How can we inspect our duplicates? 
- SELECT COUNT (DISTINCT *) FROM health.user_logs; 
- Above query can not work until a 'CTE' (common table expression) or a 'SUBQUERY' is introduced or a 'TEMPORARY TABLE' is created to instigate DISTINCT where possible (advanced), IT GOOD TO STICK TO cteS BECAUSE THEY ARE EASY TO READ AND WRITE IN MEMORY.


Data engineering - indexes and partitioning of datasets is biggest factors in DE

example of a CTE namely 'deduped_logs' to find the number of unique records

- WITH deduped_logs AS (
- SELECT DISTINCT *
- FROM health.user_logs
- ),

we can include more CTEs before the final otput to SELECT using brackets to enclose the CTEs' engines
- WITH kibe_row AS (
- SELECT COUNT(*)
- FROM schema_name.table_name
),

Then 
final output
- SELECT COUNT (*)
- FROM deduped_logs or (health.user_logs);


#### 4. Do we actually want to keep ur duplicates? important question
- GROUP BY COUNT (*) with all columns - this is important if we want to return just the duplicate data,
best way to return all data point then compare all duplicates and non duplicates.

- SELECT id,log_date, measure, measure_value, systolic, diastolic
- COUNT (*) AS record_counts
- FROM health.user_logs
- GROUP BY id, log_date, measure, measure_value, systolic, diastolic
- ORDER BY record_counts DESC;

####### NOW TO INVESTIGATE DUPLICATES
- WITH groupby_count AS (
SELECT 
id,
log_date, 
measure, 
measure_value, 
systolic, 
diastolic,
- COUNT(*) AS frequency
- FROM health.user_logs
- GROUP BY 
id, 
log_date, 
measure, 
measure_value, 
systolic, 
diastolic
),
final_output AS (
- SELECT
id, 
- COUNT(*) AS total_record_count
- FROM groupby_count
- GROUP BY id
) 
- SELECT * FROM final_output
- ORDER BY total_record_count DESC;
- (or HAVING COUNT(*) >1;)

## QUESTION WHICH id has the most duplicate values
- WITH cte_kib_count AS (
SELECT 
id,
log_date, 
measure, 
measure_value, 
systolic, 
diastolic,
- COUNT(*) AS frequency
- FROM health.user_logs
- GROUP BY 
id, 
log_date, 
measure, 
measure_value, 
systolic, 
diastolic
- HAVING COUNT(*) > 1
)
- SELECT
id, 
- SUM(frequency) AS total_duplicate_records
- - FROM cte_kib_count
- GROUP BY id
- ORDER BY total_duplicate_records DESC;

#054250c692e07a9fa9e62e345231df4b54ff435d

## QUESTION REMOVE MOST DUBLICATE ID THEN FIND LOG_DATE WITH MOST DUPLICATE VALUES

- WITH cte_kib_count AS (
- SELECT 
id,
log_date, 
measure, 
measure_value, 
systolic, 
diastolic,
- COUNT(*) AS frequency
- FROM health.user_logs
- GROUP BY 
id, 
log_date, 
measure, 
measure_value, 
systolic, 
diastolic
- HAVING COUNT(*) > 1
)
- SELECT
log_date,
- SUM(frequency) AS total_duplicate_records
- FROM cte_kib_count
- WHERE id != '054250c692e07a9fa9e62e345231df4b54ff435d'
- GROUP BY log_date
- ORDER BY total_duplicate_records DESC;
