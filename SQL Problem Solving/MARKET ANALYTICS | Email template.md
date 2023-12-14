![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/a456a42e-6a15-4013-bfa4-baef606b4c8c)

###  SQL Base Table
- DROP TABLE IF EXISTS complete_joint_dataset;
-CREATE TEMP TABLE complete_joint_dataset AS
- SELECT
-  rental.customer_id,
-  inventory.film_id,
-  film.title,
-  rental.rental_date,
-  category.name AS category_name
- FROM dvd_rentals.rental
- INNER JOIN dvd_rentals.inventory
-  ON rental.inventory_id = inventory.inventory_id
- INNER JOIN dvd_rentals.film
-  ON inventory.film_id = film.film_id
- INNER JOIN dvd_rentals.film_category
-  ON film.film_id = film_category.film_id
- INNER JOIN dvd_rentals.category
-  ON film_category.category_id = category.category_id;
- SELECT * FROM complete_joint_dataset limit 10;

## Core Calculated Fields
### 1 category_name: The name of the top 2 ranking categories
### 2 rental_count: How many total films have they watched in this category
### 3 average_comparison: How many more films has the customer watched compared to the average DVD Rental Co customer
### 4 percentile: How does the customer rank in terms of the top X% compared to all other customers in this film category?
### 5 category_percentage: What proportion of total films watched does this category make up?
  
- 
