## MINI CASE STUDY (Bitcoin Data)
- lag and lead functions 
- cumulative window functions

### problem #1 Missing Data --  Identify Null Rows
-- SELECT *
-- FROM trading.daily_btc
-- WHERE (
--  open_price + high_price + low_price +
--  close_price + adjusted_close_price + volume
-- ) IS NULL;

SOLUTION 
- USE LAG AND LEAD FUNCTIONS -- USE Lag To Fill Missing Values
- USE COALESCE FUNCTION -- USE Coalesce to Update Null Rows
## AS BELOW
- DROP TABLE IF EXISTS updated_daily_btc;
-- CREATE TEMP TABLE updated_daily_btc AS
-- SELECT
--   market_date,
--  COALESCE(
--    open_price,
--    LAG(open_price, 1) OVER w,
--    LAG(open_price, 2) OVER w
--   ) AS open_price,
--  COALESCE(
--    high_price,
--    LAG(high_price, 1) OVER w,
--    LAG(high_price, 2) OVER w
--  ) AS high_price,
--  COALESCE(
 --   low_price,
--    LAG(low_price, 1) OVER w,
--    LAG(low_price, 2) OVER w
--  ) AS low_price,
--  COALESCE(
--    close_price,
--    LAG(close_price, 1) OVER w,
--    LAG(close_price, 2) OVER w
--  ) AS close_price,
--  COALESCE(
--    adjusted_close_price,
--    LAG(adjusted_close_price, 1) OVER w,
--    LAG(adjusted_close_price, 2) OVER w
--  ) AS adjusted_close_price,
--  COALESCE(
--    volume,
--    LAG(volume, 1) OVER w,
--    LAG(volume, 2) OVER w
--  ) AS volume
--FROM trading.daily_btc
-- NOTE: checkout the syntax where I've included an unused window below!
-- WINDOW
--  w AS (ORDER BY market_date),
 -- unused_window AS (ORDER BY market_date DESC);

-- inspect a few rows of the updated dataset for October
-- SELECT *
--  FROM updated_daily_btc
-- WHERE market_date BETWEEN '2020-10-08'::DATE AND '2020-10-15'::DATE;

### So if we wanted to perform a cumulative sum calculation, adding the previous volume amounts to a running total OF OUR DATASET  - WE USE a single CTE volume_data with our first 10 rows of volume data.

-- WITH volume_data AS (
--  SELECT
--   market_date
-- volume
--  FROM updated_daily_btc
--  ORDER BY market_date
--  LIMIT 10
-- )
-- SELECT
--   t1.market_date,
--   t1.volume,
--   SUM(t2.volume) AS running_total
-- FROM volume_data t1
-- INNER JOIN volume_data t2
-- ON t1.market_date >= t2.market_date
-- GROUP BY 1,2
-- ORDER BY 1,2;

### OR CUMULATIVE SUM AS BELOW
-- WITH volume_data AS (
--  SELECT
--    market_date,
--    volume
-- FROM updated_daily_btc
--  ORDER BY market_date
-- LIMIT 10
-- )
-- SELECT
-- market_date,
--  volume,
--  SUM(volume) OVER (ORDER BY market_date) AS cumulative_sum
-- FROM volume_data;

TASK ANSWERED BY ABOVE COMPUTATIONS
#### 1 What is the earliest and latest market_date values?
#### 2 What was the historic all-time high and low values for the close_price and their dates?
#### 3 Which date had the most volume traded and what was the close_price for that day?
#### 4 How many days had a low_price price which was 10% less than the open_price?
#### 5 What percentage of days have a higher close_price than open_price?
#### 6 What was the largest difference between high_price and low_price and which date did it occur?
#### 7 If you invested $10,000 on the 1st January 2016 - how much is your investment worth in 1st of February 2021? Use the close_price for this calculation
