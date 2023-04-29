### HOW many records(rows)?

#### example How many rows are there in the row_name? i.e
- SELECT 
- COUNT (*) AS row_count  ( some use COUNT (1) ) but it is slower
FROM schema_name.table_name

### UNIQUE COMLUMN VALUES

- SELECT 
- DISTINCT rating
- if count of unique values COUNT (DISTINCT category)AS item_name etc
- FROM dvd_rentals.film_list (removes diplucates)

### GROUP BY COUNT
- IF QUESTION asks frequency it is asking for the COUNT, does not check for null
- Most important thing to note, for 'group by' only 1 row of each group is returned

### 'GROUP BY' EXAMPLE 
