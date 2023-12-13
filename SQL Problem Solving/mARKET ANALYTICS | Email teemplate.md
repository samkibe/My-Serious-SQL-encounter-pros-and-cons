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
