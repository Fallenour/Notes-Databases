# Notes-Databases

https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-22-04-quickstart

https://www.digitalocean.com/community/tutorials/how-to-install-mariadb-on-ubuntu-22-04

https://www.guru99.com/mariadb-vs-mysql.html

https://docs.digitalocean.com/products/databases/postgresql/how-to/manage-connection-pools/

https://www.enterprisedb.com/postgres-tutorials/why-you-should-use-connection-pooling-when-setting-maxconnections-postgres

https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-elasticsearch-on-ubuntu-22-04

### MariaDB

# Grant Admin access 
GRANT ALL ON *.* TO '<username>'@'localhost' IDENTIFIED BY '<password>' WITH GRANT OPTION;

# Create Databases
  CREATE DATABASE <databasename> COMMENT '<commenthere>';
  
# Alter Databases
  ALTER DATABASE <databasename> <COMMAND> <variables>
  eg;
  ALTER DATABASE test COMMENT 'this database is a test db';

# How to set a global Value for configs
SET GLOBAL <valuename>=<value>;
eg;
SET GLOBAL userstat=1;

#list of values that can be set
https://mariadb.com/kb/en/server-system-variables/#userstat

# Show Databases
- SHOW DATABASES;
- SHOW DATABASES LIKE 'm%';

# Show Statistics
SHOW USER_STATISTICS\G;
SELECT * FROM INFORMATION_SCHEMA.USER_STATISTICS\G;

SHOW CLIENT_STATISTICS\G;
SELECT * FROM INFORMATION_SCHEMA.CLIENT_STATISTICS\G;

SELECT * FROM INFORMATION_SCHEMA.INDEX_STATISTICS WHERE TABLE_NAME = "author";
SELECT * FROM INFORMATION_SCHEMA.TABLE_STATISTICS WHERE TABLE_NAME='user';




# Show Engines
SHOW ENGINES;

# Show Slaves
SHOW ALL SLAVES STATUS;
SHOW ALL REPLICAS STATUS -- From MariaDB 10.5.1;

# Show Tables

SHOW TABLEs in <databasename>;
eg.
SHOW TABLES in test;
  
# Show Table Status
SHOW TABLE STATUS in <databasename>;
eg.
SHOW TABLE STATUS in test;

# Show Warnings
SHOW WARNINGS;
SHOW COUNT(*) WARNINGS;

# Show Errors
SHOW ERRORS;
SHOW COUNT(*) ERRORS;

# Show Master Status
SHOW MASTER STATUS;
SHOW BINLOG STATUS -- From MariaDB 10.5.2;


# MariaDB Sources
https://mariadb.com/kb/en/create-database/
https://mariadb.com/kb/en/alter-database/
https://mariadb.com/kb/en/show-databases/
https://mariadb.com/kb/en/show-replica-status/
https://mariadb.com/kb/en/show-table-status/
https://mariadb.com/kb/en/show-tables/
https://mariadb.com/kb/en/show-user-statistics/
https://mariadb.com/kb/en/user-statistics/#userstat
https://mariadb.com/kb/en/show-warnings/
https://mariadb.com/kb/en/show-binlog-status/
https://mariadb.com/kb/en/show-errors/
https://mariadb.com/kb/en/show-engines/


https://mariadb.com/kb/en/server-system-variables/#userstat


# Elasticsearch

# Installing Elasticsearch
- https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-elasticsearch-on-ubuntu-22-04

## Get Elasticsearch GPG Key
- curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elastic.gpg

## Configre Debian Package Repo for Elasticsearch Repository

- echo "deb [signed-by=/usr/share/keyrings/elastic.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list

## Update Package Repo and install Elasticsearch from Repo
- sudo apt update
- sudo apt install elasticsearch

## Configure basic networking function for Elasticsearch

- sudo nano /etc/elasticsearch/elasticsearch.yml
-- Change network.host setting from IP address to localhost

## Start the Elasticsearch Application, and set it to autorun on startup
- sudo systemctl start elasticsearch
- sudo systemctl enable elasticsearch
