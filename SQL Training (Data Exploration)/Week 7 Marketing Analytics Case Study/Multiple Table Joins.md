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
