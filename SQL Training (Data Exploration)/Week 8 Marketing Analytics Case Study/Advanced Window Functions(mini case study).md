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

#### What is the earliest and latest market_date values?
#### What was the historic all-time high and low values for the close_price and their dates?
#### Which date had the most volume traded and what was the close_price for that day?
#### How many days had a low_price price which was 10% less than the open_price?
#### What percentage of days have a higher close_price than open_price?
#### What was the largest difference between high_price and low_price and which date did it occur?
#### If you invested $10,000 on the 1st January 2016 - how much is your investment worth in 1st of February 2021? Use the close_price for this calculation
