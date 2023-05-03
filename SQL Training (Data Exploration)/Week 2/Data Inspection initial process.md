### Data Inspection with examples

## 1. IF measure_value = 0 
(Measure in this case is an entity in the Health analytics Data)
introduces a 'WHERE CLAUSE' to keep only values which meet a logical condition, the 'WHERE' filter is supposed to be after the 'FROM'
par exemple' 
- SELECT * 
- FROM schema_name.table.name
- WHERE measure-value = 0

- SELECT * 
- FROM health.user_logs
- WHERE measure_value = 0;

question - Look for values where the measure-value = 0
- SELECT measure, 
- COUNT (*)
- FROM health.user_logs
- WHERE measure_value = 0
- GROUP BY measure;

## IF measure _value = 'blood pressure'
example 
- SELECT *
- FROM health.user_logs
- WHERE measure = 'blood_pressure'; we should use quotes if we are looking for a string in the column

## WHERE LOOKING FOR BOTH 'measure & measure_value' ( WE use AND) 
In other cases we use AND,&&,OR WHERE either CONDITIONs are TRUE
example
- SELECT *
- FROM health.user_logs
- WHERE measure = 'blood_pressure' 
- AND measure_value = 0;

## WHERE there is 'NULL' values
- SELECT *
- FROM schema.name.table.name
- WHERE table.name is NULL
example for real data
- SELECT *
- FROM health.user_logs
- WHERE systolic is NULL; 
for null
- SELECT measure, COUNT(*)
- FROM health.user_logs
- WHERE systolic is NULL OR systolic = 0
- GROUP BY measure; 




