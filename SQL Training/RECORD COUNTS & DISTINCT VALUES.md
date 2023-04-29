### HOW many records (rows)?

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
What is the 'frequency' of values in the rating column in the film table?
- SELECT rating
- COUNT (*)
- FROM dvd_rentals.film_list
- GROUP BY rating
#### NOTE ( 'group by' has to be after the 'from', and 'order by' has to be after the the 'group by', 'limits' after the 'order by', 'where - filters' between the 'from' and 'group by'

# STRUCTURE OF SQL Query as follows in order
- SELECT
- FROM
- WHERE Filters
- GROUP BY
- ORDER BY
- LIMITS

#### EXAMPLE of a recommmended syntax
- SELECT 
- rating, category
- COUNT(*) AS frequency
- FROM dvd_rental.film-list
- GROUP BY rating, category
- ORDER BY frequency DESC
- LIMIT 5;

#### WORKED 
Question What are the 5 most frequent rating and category combination in the film_list table?
- SELECT
- rating, category,
- COUNT(*) AS frequency
- FROM dvd_rentals.film_list
- GROUP BY rating, category
- ORDER BY frequency DESC
- LIMIT 5;

