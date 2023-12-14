- DROP TABLE IF EXISTS updated_daily_btc;
- CREATE TEMP TABLE updated_daily_btc AS
- SELECT
-   market_date,
-   COALESCE(
-    open_price,
-    LAG(open_price, 1) OVER w,
-    LAG(open_price, 2) OVER w
-  ) AS open_price,
-    COALESCE(
-    high_price,
-    LAG(high_price, 1) OVER w,
-   LAG(high_price, 2) OVER w
-  ) AS high_price,
-  COALESCE(
-    low_price,
-    LAG(low_price, 1) OVER w,
-    LAG(low_price, 2) OVER w
-  ) AS low_price,
-  COALESCE(
-    close_price,
-    LAG(close_price, 1) OVER w,
-    LAG(close_price, 2) OVER w
-  ) AS close_price,
-  COALESCE(
-    adjusted_close_price,
-    LAG(adjusted_close_price, 1) OVER w,
-   LAG(adjusted_close_price, 2) OVER w
- ) AS adjusted_close_price,
-  COALESCE(
-    volume,
-    LAG(volume, 1) OVER w,
-    LAG(volume, 2) OVER w
-  ) AS volume
- FROM trading.daily_btc
- WINDOW
-  w AS (ORDER BY market_date),
-  unused_window AS (ORDER BY market_date DESC);

### 1 What is the average daily volume of Bitcoin for the last 7 days?
### 2 Create a 1/0 flag if a specific day is higher than the last 7 days volume average
### 3 What is the percentage of weeks (starting on a Monday) where there are 4 or more days with increased volume?
### 4 How many high volume weeks are there broken down by year for the weeks with 5-7 days above the 7 day volume average excluding 2021?

## solution for part 1 and 2
