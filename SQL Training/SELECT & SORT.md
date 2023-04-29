# SELECT STATEMENTS
1. ### SELECT
- col_name, (commas are very important)
- col_name

##### incase we want every item on a table
- * we use an 'asterisk' for all
##### incase we want a particular or specific item on a table we use the item ID
- item_id

2. ### FROM 
- schema_name.table_name; (the semi colon and the end of the query helps the system to know where the query ends)
- schema.name identifies the schema then (.) table in that schema in a case where there is multiple schemas or in a broad DB.

3. ### LIMIT X; 
- IF WE DO NOT KNOW THE AMOUNT OF THE DATA OR COLUMNS WE USE 'LIMIT' SO THAT we do not CRASH THE SYSTEM. It's of best practise to always use a limit.

# SORTING TEXT COLUMN
4. ### ORDER BY
- When sorting we, basically use order by at default which gives results or output in alphabetical order.

## example query with all above intergrated 📧
- SELECT country
- FROM dvd-rental.country
- ORDER BY country
- LIMIT 5;
