#### We have been asked to support the customer analytics team at DVD Rental Co who have been tasked with generating the necessary data points required to populate specific parts of this first-ever customer email campaign.

## Training objective
--- Understanding the Data - Data exploration - Data inspection
### Tables needed
- Rentals (SELECT *FROM dvd_rentals.rental WHERE customer_id = 130;)
- Inventory (SELECT * FROM dvd_rentals.inventory WHERE film_id = 1;)
- Film (SELECT * FROM dvd_rentals.film LIMIT 5;)
- Film_category (SELECT * FROM dvd_rentals.film_category LIMIT 5;)
- Category (SELECT * FROM dvd_rentals.category LIMIT 5;)
- Film_actor (SELECT * FROM dvd_rentals.film_actor WHERE actor_id = 1;)
- Actor (SELECT * FROM dvd_rentals.actor LIMIT 5;)

### Step 1 Real campaign Analyst Project
- WHO?  for who is this analysis being done
- WHAT? EG fill an email template, explore
- WHERE? from where are we running the data from for my case i am running from BIGQUERY.
- WHEN? Check timelines, when to handover, or transition points
- WHY? the value this analysis might bring, and the purpose

### Step 2 IDENTIFY THE REQUIREMENT
- Requirement #1 Top 2 - Categories For each customer-  we need to identify the top 2 categories for each customer based off their past rental history. 
- Requirement #2 - Category Film Recommendations - The marketing team has also requested for the 3 most popular films for each customer’s top 2 categories
- Requirement #3 & #4 -Individual Customer Insights  The number of films watched by each customer in their top 2 categories is required as well as some specific insights.
  
- For the 1st category, the marketing requires the following insights (requirement 3):
###How many total films have they watched in their top category?
###How many more films has the customer watched compared to the average DVD Rental Co customer?
###How does the customer rank in terms of the top X% compared to all other customers in this film category?

###For the second ranking category (requirement 4):
###How many total films has the customer watched in this category?
###What proportion of each customer’s total films watched does this count make?



### Step 3 THEN DRAW AN ENTITY RELATIONSHIP DI8AGRAM

# Results. 
You’ve watched {rental_count} {category_name} films, that’s {average_comparison} more than the Dvd Rental Co average and puts you in the top {percentile}% of {category_name} gurus!

You’ve watched {rental_count} {category_name} films making up {category_percentage}% of your entire viewing history!

You’ve watched <rental_count> films featuring <actor_name>! Here are some other films <first_name> stars in that might interest you!
