Sql injection
``` bash
sqlmap --wizard

# extract all database names
--dbs 

# extract information about the tables of that database by using
-D database_name --tables

# enumerate the records in those tables
-D database_name -T table_name --dump

# test GET parameter URL
-u

# add cookie
--cookie
```