Creating an email template as below for Market analytics

![Uploading image.png…]()
Table Joining Journey

#### Join Journey Part	| Start |            	End	  | Foreign Key
- Part 1	                - rental	       - inventory	- inventory_id
- Part 2	                - inventory   	- film	- film_id
- Part 3	                - film	        - film_category	- film_id
- Part 4                	- film_category - category	- category_id
- 
#### The key columns that we will need to generate include the following data points at a customer_id level:

- category_name: The name of the top 2 ranking categories
- rental_count: How many total films have they watched in this category
- average_comparison: How many more films has the customer watched compared to the 
- average DVD Rental Co customer
- percentile: How does the customer rank in terms of the top X% compared to all other customers in this film category?
- category_percentage: What proportion of total films watched does this category make up?

#### THEN We need to generate the rental_count calculation - the number of films that a customer has watched in a specific category.
- EG SELECT
 customer_id,
  COUNT(*) AS rental_count
FROM `dvd_rentals.rental`
GROUP BY
  customer_id;
- OR SHOW Show ALL rentals made by A CUSTOMER USING THEIR ID EG customer_id = 130:
- SELECT *
FROM dvd_rentals.rental
WHERE customer_id = 130;

#### Validating Hypotheses with Data
###### (OF ITEMS WHICH NEVER SOLD OR OTHERWISE) by using a WHERE NOT EXIST (ANTI JOIN) for our case this dvd never was rented
- SELECT * FROM dvd_rentals.inventory
WHERE NOT EXISTS (
  SELECT 1 -- THIS SUBQUERY DOESNT RETURN ANYTHING
  FROM dvd_rentals.rental
  WHERE inventory.inventory_id = rental.inventory_id

#### hypothesis 1 : The number of unique inventory_id records will be equal in both dvd_rentals.rental and dvd_rentals.inventory tables if not then there exist an item on the DB THAT IS UNIQUE OR INACTIVE and we find it using above subquery. below are subqueries to satisfy equality.
- SELECT
  COUNT(DISTINCT inventory_id)
FROM dvd_rentals.rental;
- SELECT
  COUNT(DISTINCT inventory_id)
FROM dvd_rentals.inventory;

### hypothesis 2 : There will be a multiple records per unique inventory_id in the dvd_rentals.rental table
- SELECT inventory_id, COUNT (*) AS record_counts
  FROM dvd_rentals.rental
  GROUP BY inventory_id
  ORDER BY record_counts desc;

-  WITH cte_counts AS ( 
  SELECT inventory_id, COUNT (*) AS record_counts
  FROM dvd_rentals.rental
  GROUP BY inventory_id
) 
SELECT
  record_counts,
  COUNT(*) as unique_inventory_ids
FROM cte_counts
GROUP BY record_counts
ORDER BY record_counts;

### Hypothesis 3 : There will be multiple inventory_id records per unique film_id value in the dvd_rentals.inventory table. WHAT INVENTORY EXIST IN STORE!!!
- SELECT
  film_id,
  COUNT(DISTINCT inventory_id) 
  FROM dvd_rentals.inventory
GROUP BY film_id
ORDER BY 2 DESC;
#### using WITH cte 
- WITH cte_counts AS (
  SELECT
  film_id,
  COUNT(DISTINCT inventory_id) AS unique_record_counts
  FROM dvd_rentals.inventory
GROUP BY film_id
)
-- summarize the group by counts above by grouping again on the row_counts from counts_base CTE part
SELECT
  unique_record_counts,
  COUNT(*) as film_id
FROM cte_counts
GROUP BY unique_record_counts
ORDER BY unique_record_counts desc;
#### LEFT join 
- -- how many foreign keys only exist in the left table and not in the right?
- SELECT
  COUNT(DISTINCT rental.inventory_id)
FROM dvd_rentals.rental
WHERE NOT EXISTS (
  SELECT inventory_id
  FROM dvd_rentals.inventory
  WHERE rental.inventory_id = inventory.inventory_id
);

