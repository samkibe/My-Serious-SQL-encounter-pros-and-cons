## Marketing Analytics || Email template

### SQL Engineering / architecture - Sitation Task Action Results (STAR)
- P- Problem -- context of the task
- E- Exploration
- A- Analysis - what is the plan ?
- R- Report - what to do with results/ final delivery

# P- Problem -- context of the task

![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/ff6dedfd-bac8-4ab1-b213-1c52b271a1b6)

# E- Exploration
![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/b091b1f4-b9c1-4a27-8199-17a8c3051204)

![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/6eb73093-d833-4cea-b510-d881d3aba762)

# A- Analysis - what is the plan ?

## actor to film relationship
- WITH actor_film_counts AS (
-  SELECT
-    actor_id,
-    COUNT(DISTINCT film_id) AS film_count
-  FROM dvd_rentals.film_actor
-  GROUP BY actor_id
- )
- SELECT
-    film_count,
-  COUNT(*) AS total_actors
- FROM actor_film_counts
- GROUP BY film_count
- ORDER BY film_count DESC;
  
## film to actor relationship
- WITH film_actor_counts AS (
-   SELECT
-   film_id,
-   COUNT(DISTINCT actor_id) AS actor_count
-  FROM dvd_rentals.film_actor
-  GROUP BY film_id
- )
- SELECT
-  actor_count,
-  COUNT(*) AS total_films
- FROM film_actor_counts
- GROUP BY actor_count
- ORDER BY actor_count DESC;
