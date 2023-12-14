### Window Frame Components
![image](https://github.com/samkibe/My-Serious-SQL-encounter-pros-and-cons/assets/25104443/23d7a06a-c119-4f86-95f8-3a2035d6410f)

- The first thing to know about the FRAME clause is what is actually used as default when we do not explicitly specify them in our window functions.
### As stated in the components - the default is:( RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW )
- SELECT
-  market_date,
-  volume,
-  SUM(volume) OVER (ORDER BY market_date) AS cumulative_sum,
-  SUM(volume) OVER (
-    ORDER BY market_date
-    RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
-  ) AS default_cumulative_sum
- FROM updated_daily_btc
- ORDER BY market_date
- LIMIT 10;
