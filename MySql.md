## MySql

-   Connect to a db:  
    `mysql -udb_name -ppwd`
-   Remove liquibase lock:

```sql
UPDATE CONFIGURATION_ADMINISTRATION_DATABASECHANGELOGLOCK
SET LOCKED=0, LOCKGRANTED=null, LOCKEDBY=null ;
```

-   clean db:

```sql
DROP database db_name;
CREATE database db_name;
```

-   select db:  
    `use db_name;`
-   List tables:  
    `show tables;`
