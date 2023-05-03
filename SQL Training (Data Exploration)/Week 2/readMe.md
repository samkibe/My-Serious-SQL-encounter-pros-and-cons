### Used Health analytics Data
#### What to check/investigate first, when exploring a new Dataset.
- Show 1st few rows using 'LIMIT' and all columns using 'SELECT (*)'
- Find out how many records are there using 'COUNT (*)'
- Any other things 'of' interest

### Further AnalYsis
- COUNT (*) & COUNT DISTINCT to find columns of interest
- Percetage calculation using window function ( COUNT (*) / divide by SUM(COUNT (*) ) over(empty partition)
- Investigate specific values

### Data Inspection
- measure_value = 0 introduces a 'WHERE CLAUSE' to keep only values which meet a logical condition, the 'WHERE' filter is supposed to be after the 'FROM'
- par exemple' 
- SELECT * 
- FROM schema_name.table.name
- WHERE measure-value = 0

- SELECT * 
- FROM health.user_logs
- WHERE measure_value = 0;

Look for values where the measure-value = 0
- SELECT measure, 
- COUNT (*)
- FROM health.user_logs
- WHERE measure_value = 0
- GROUP BY measure;

