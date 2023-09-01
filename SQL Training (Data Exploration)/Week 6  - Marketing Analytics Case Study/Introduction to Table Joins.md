SQL TABLE JOIN
### -- sample table
DROP TABLE IF EXISTS names;
CREATE TEMP TABLE names AS
WITH input_data (iid, first_name, title) AS (
 VALUES
 (1, 'Kate', 'Datacated Visualizer'),
 (2, 'Eric', 'Captain SQL'),
 (3, 'Danny', 'Data Wizard Of Oz'),
 (4, 'Ben', 'Mad Scientist'),
 (5, 'Dave', 'Analytics Heretic'),
 (6, 'Ken', 'The YouTuber')
)
SELECT * FROM input_data;

DROP TABLE IF EXISTS jobs;
CREATE TEMP TABLE jobs AS
WITH input_data (iid, occupation, salary) AS (
 VALUES
 (1, 'Cleaner', 'High'),
 (2, 'Janitor', 'Medium'),
 (3, 'Monkey', 'Low'),
 (6, 'Plumber', 'Ultra'),
 (7, 'Hero', 'Plus Ultra')
)
SELECT * FROM input_data;
Inspecting the names table
## INNER JOIN
SELECT
  names.iid,
  names.first_name,
  names.title,
  jobs.occupation,
  jobs.salary
FROM names
INNER JOIN jobs
  ON names.iid = jobs.iid;

## LEFT JOIN // LEFT OUTER JOIN NO RIGHT JOIN
SELECT names.iid, names.first_name, names.title,jobs.occupation,jobs.salary
FROM names
LEFT JOIN jobs
  ON names.iid = jobs.iid;
  
## FULL JOIN // FULL OUTER JOIN 
SELECT
  names.iid AS name_id,
  jobs.iid AS job_id,
  names.first_name,
  names.title,
  jobs.occupation,
  jobs.salary
FROM names
FULL JOIN jobs
  ON names.iid = jobs.iid;
## CROSS JOIN // FROM Table1,Table2  avoid it if necessary
SELECT
  names.iid as name_iid,
  jobs.iid as job_iid,
  names.first_name,
  names.title,
  jobs.occupation,
  jobs.salary
FROM names
CROSS JOIN jobs;

## LEFT SEMI JOIN
SELECT
  names.iid,
  names.first_name
FROM names
WHERE EXISTS (
  SELECT iid
  FROM new_jobs
  WHERE names.iid = new_jobs.iid
);

- LEFT JOIN with a DISTINCT followed by a WHERE filter to remove all null values from the resulting joint dataset.

- SELECT DISTINCT
  names.iid,
  names.first_name
FROM names
LEFT JOIN new_jobs
  ON names.iid = new_jobs.iid
WHERE new_jobs.iid IS NOT NULL;

## ANTI JOIN
SELECT
  names.iid,
  names.first_name
FROM names
WHERE NOT EXISTS (
  SELECT 1
  FROM new_jobs
  WHERE names.iid = new_jobs.iid
);
