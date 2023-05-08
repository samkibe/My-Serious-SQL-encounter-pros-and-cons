SELECT &  SORT
- Basic SELECT eg (SELECT * FROM health.user_logs;)
- LIMIT When we do not know the size of the data its good to limit results so that we do not crash the system. eg (LIMIT 10;)
- ORDER BY ASC/DESC eg (ORDER BY measure DESC;)
Example code ; -
- SELECT measure 
- FROM health.user_logs
- ORDER BY measure DESC
- LIMIT 10;
