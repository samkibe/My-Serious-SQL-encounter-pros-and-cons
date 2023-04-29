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
- When sorting we basically use 'order by' at default, whose results or output is in ascending alphabetical order. However we can include DESC to sort in descending or reverse order.

## example query with all above intergrated 📧
- SELECT country
- FROM dvd-rental.country
- ORDER BY country DESC
- LIMIT 5;

# Cool example of SORT & LIMIT
#### What are the 5 lowest total-sales values in the sales_by_film_category table?
- SELECT total_sales
- FROM dvd-rentals.sales_by_film_category
- ORDER BY 1 (for 5 highest we might want to include DESC after 1, my view)
- LIMIT 5;
