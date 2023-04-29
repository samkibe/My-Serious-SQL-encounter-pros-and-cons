# SQL Environment

Will consit of two Docker containers, a database to hold our projects's Data, and a Graphical user interface GUI to write and run sql queries (SQLPad)

relevant commands
- docker-compose up - on terminal to create db and still access the docker container
(Navigate to the serious-sql folder where docker-compose.yml lives in the explorer
Click on the address bar, in Windows Explorer, Type 'cmd' in the address bar and hit Enter (then on cmd at the docker environment type 'docker-compose up' and hit enter))
-After 'docker-compose up' runs it will initiate a prompt (Database system is ready to accept connections) now enter 'http://localhost:3000/' - on the browser and the SQL Pad will pop up.
- to update Docker images - the docker-compose.yml file must be updated often times.
- docker ps - o check if are active
