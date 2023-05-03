### QUESTIONS
#### 1. How can we identify duplicates?
IDENTIFICATION OF DUPLICATES
- Row counts vs distinct row counts (select distinct *)
example 
- SELECT COUNT (*) FROM health.user_logs;

#### 2. Should we remove all of them NO - apply DISTINCT to wipe, although inspect data first
#### 3. How can we inspect our duplicates? 
- SELECT COUNT (DISTINCT *) FROM health.user_logs; 
Above query can not work until a 'CTE' (common table expression) or a 'SUBQUERY' is introduced or a 'TEMPORARY TABLE' is created to instigate DISTINCT where possible (advanced)
Data engineering - indexes and partitioning of datasets is biggest factors in D

example of a CTE

- WITH deduped_logs AS (
- SELECT DISTINCT *
- FROM health.user_logs
- ),

#### 4. Do we actually want to keep ur duplicates? important question
